---
title: 保護 WCF Data Services 的安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: cf99979e2ea3a47247a5df4b6e0ececab6abe8ef
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645521"
---
# <a name="securing-wcf-data-services"></a>保護 WCF Data Services 的安全
本主題描述專屬於開發、 部署和執行 WCF 資料服務和應用程式服務支援開放式資料通訊協定 (OData) 所存取的安全性考量。 您也應該遵循建立安全的.NET Framework 應用程式的建議。  
  
在規劃如何保護 WCF Data Services 為基礎的 OData 服務時，您必須處理驗證、 探索與確認主體的身分識別的程序和授權程序可決定是否已驗證的主體允許存取要求的資源。 您也應該考慮是否要使用 SSL 加密訊息。  
  
## <a name="authenticating-client-requests"></a>驗證用戶端要求  
WCF 資料服務不會實作任何一種自己的驗證，但是會依賴資料服務主機的驗證提供。 這表示服務會假設它所接收的任何要求的網路主機中已經過驗證，而且該主機已正確識別的原則要求 WCF 資料服務所提供的介面。 這些驗證選項和方法詳述於 multipart [OData 和驗證數列](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)。  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>用於 WCF Data Service 的驗證選項  
 下表列出了一些驗證機制，可協助您驗證 WCF Data Service 的要求。  
  
|驗證選項|描述|  
|----------------------------|-----------------|  
|匿名驗證|啟用 HTTP 匿名驗證時，任何原則都可以連線至資料服務。 匿名存取不需要認證。 只有在您想要允許任何人存取資料服務時，才使用此選項。|  
|基本和摘要式驗證|驗證需要使用者名稱和密碼所組成的認證。 支援非 Windows 用戶端的驗證。 **安全性注意事項：** 基本驗證認證 (使用者名稱和密碼) 會以純文字傳送，而且可以被攔截。 摘要式驗證會根據所提供的認證傳送雜湊，這讓它比基本驗證更安全。 兩者都很容易受到攔截式攻擊。 使用這些驗證方法時，您應該考慮使用安全通訊端層 (SSL)，加密用戶端與資料服務之間的通訊。 <br /><br /> Microsoft Internet Information Services (IIS) 提供實作這兩個基本和摘要式驗證的 HTTP 要求的 ASP.NET 應用程式中。 這個 Windows 驗證提供者實作可讓 .NET Framework 用戶端應用程式將要求之 HTTP 標頭中的認證提供給資料服務，以便密切地交涉 Windows 使用者的驗證。 如需詳細資訊，請參閱 <<c0> [ 摘要式驗證技術參考](https://go.microsoft.com/fwlink/?LinkId=200408)。<br /><br /> 當您想要有您的資料服務使用基本驗證根據一些自訂的驗證服務和非 Windows 認證時，您必須實作自訂的 ADP.NET HTTP 模組進行驗證。<br /><br /> 如需如何使用自訂基本驗證配置搭配 WCF Data Services 的範例，請參閱部落格文章[OData 和驗證 – 第 6 部分-自訂基本驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/)。|  
|Windows 驗證|Windows 型認證是使用 NTLM 或 Kerberos 交換。 此機制比基本或摘要式驗證更安全，但它需要用戶端是 Windows 架構的應用程式。 IIS 也會提供 HTTP 要求的 ASP.NET 應用程式中的 Windows 驗證的實作。 如需詳細資訊，請參閱 < [ASP.NET 表單驗證概觀](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100))。<br /><br /> 如需如何搭配 WCF Data Services 使用 Windows 驗證的範例，請參閱部落格文章[OData 和驗證 – 第 2 篇-Windows 驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/)。|  
|ASP.NET 表單驗證|表單驗證可讓您使用自己的程式碼來驗證使用者，然後在 Cookie 或網頁 URL 中維護驗證語彙基元 (Token)。 您可以使用您所建立的登入表單驗證使用者的使用者名稱和密碼。 未經驗證的要求會重新導向至登入頁面，使用者可在此處提供認證和送出表單。 如果應用程式驗證了要求，則系統會發出包含金鑰的票證，用於重新建立後續要求的身分識別。 如需詳細資訊，請參閱 <<c0> [ 表單驗證提供者](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100))。 **安全性注意事項：** 根據預設，包含表單驗證票證的 cookie 並不安全的 ASP.NET Web 應用程式中使用表單驗證時。 您應該考慮要求 SSL 同時保護驗證票證和初始登入認證。 <br /><br /> 使用方式的範例表單與 WCF Data Services 的驗證，請參閱部落格文章[OData 和驗證 – 第 7 – 表單驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/)。|  
|宣告架構驗證|在宣告型驗證中，資料服務所依賴的受信任 「 協力廠商 」 身分識別提供者服務來驗證使用者。 身分識別提供者會明確地驗證要求資料服務資源之存取權的使用者，並發出授與要求資源之存取權的語彙基元。 接著，系統會向資料服務呈現此權杖，然後根據與發出存取權杖之身分識別服務的信任關係，授與存取權給使用者。<br /><br /> 使用宣告架構驗證提供者的優點是，它們可以跨信任網域，用來驗證各種不同類型的用戶端。 資料服務可以採用此種協力廠商提供者，來卸載維護和驗證使用者的需求。 OAuth 2.0 是 Microsoft Azure AppFabric 存取控制所支援的宣告架構驗證通訊協定，以服務的方式用於聯盟授權。 此通訊協定支援 REST 型服務。 如需如何搭配 WCF Data Services 中使用 OAuth 2.0 的範例，請參閱部落格文章[OData 和驗證 – 第 8 部分-OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/)。|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>用戶端程式庫中的驗證  
 根據預設，WCF Data Services 用戶端程式庫不提供認證至 OData 服務提出要求時。 當資料服務需要登入認證來驗證使用者時，這些認證可以在從 <xref:System.Net.NetworkCredential> 之 <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> 屬性存取的 <xref:System.Data.Services.Client.DataServiceContext> 中提供，如以下範例所示：  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 如需詳細資訊，請參閱[如何：指定的資料服務要求用戶端認證](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)。  
  
 當資料服務需要無法使用 <xref:System.Net.NetworkCredential> 物件指定的登入認證 (例如宣告架構語彙基元或 Cookie) 時，您必須在 HTTP 要求中手動設定標頭，這通常是 `Authorization` 和 `Cookie` 標頭。 如需有關此種驗證案例的詳細資訊，請參閱部落格文章[OData 和驗證 – 第 3 篇 – 用戶端攔截](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/)。 如需如何設定 HTTP 標頭的要求訊息中的範例，請參閱[How to:設定用戶端要求中的標頭](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)。  
  
## <a name="impersonation"></a>模擬  
 一般而言，資料服務會使用裝載資料服務之背景工作處理序的認證來存取所需的資源，例如伺服器或資料庫上的檔案。 使用模擬時，可以用提出要求之使用者的 Windows 識別身分 (使用者帳戶) 執行 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式。 模擬常用於依賴 IIS 驗證使用者，而且此原則的認證用來存取必要資源的應用程式。 如需詳細資訊，請參閱 < [ASP.NET 模擬](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100))。  
  
## <a name="configuring-data-service-authorization"></a>設定資料服務授權  
 授權是將應用程式資源的存取權授與根據先前成功驗證所識別的原則或過程。 一般的作法是，您應該只授與足夠的權限給資料服務的使用者來執行用戶端應用程式所需的作業。  
  
### <a name="restrict-access-to-data-service-resources"></a>限制資料服務資源的存取  
 根據預設，WCF Data Services 可讓您授與一般讀取和寫入權限，針對資料服務資源 （實體集和服務作業），任何能夠存取資料服務的使用者。 定義讀取和寫入權限的規則可以針對資料服務所公開的每個實體，以及公開到任何服務作業的每個實體個別定義。 建議您同時將讀取和寫入權限僅限為用戶端應用程式所需的資源。 如需詳細資訊，請參閱 <<c0> [ 最少資源存取需求](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)。  
  
### <a name="implement-role-based-interceptors"></a>實作以角色為基礎的攔截器  
 攔截器可讓您在資料服務實際運作之前，攔截對資料服務資源的要求。 如需詳細資訊，請參閱 <<c0> [ 攔截器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。 攔截器可讓您根據提出要求的已驗證使用者進行授權決策。 如需如何限制存取資料服務資源，根據已驗證的使用者身分識別的範例，請參閱[How to:攔截資料服務訊息](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>限制已保存之資料存放區和本機資源的存取  
 用來存取已保存之存放區的帳戶應該僅被授與資料庫或檔案系統中的足夠權限來支援資料服務的需求。 使用匿名驗證時，這是用來執行裝載應用程式的帳戶。 如需詳細資訊，請參閱[如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。 使用模擬時，必須將這些資源的存取權授與已驗證的使用者，通常是做為 Windows 群組的一部分。  
  
## <a name="other-security-considerations"></a>其他安全性考量  
  
### <a name="secure-the-data-in-the-payload"></a>保護裝載中資料的安全  
OData 是以 HTTP 通訊協定為基礎。 在 HTTP 訊息中，根據資料服務實作的驗證，標頭可能包含寶貴的使用者認證。 訊息主體可能也包含必須受到保護的寶貴客戶資料。 在這兩種情況下，建議您使用 SSL 透過網路傳輸保護這項資訊。  
  
### <a name="ignored-message-headers-and-cookies"></a>已忽略的訊息標頭和 Cookie  
 資料服務會忽略，而且絕不會設定宣告內容類型與資源位置以外之標頭的 HTTP 要求標頭。  
  
 Cookie 可用來當做組件的驗證配置，例如使用 ASP.NET 表單驗證。 不過，WCF DataServices 會忽略在連入要求上設定的所有 HTTP cookie。 資料服務的主機可能會處理 cookie，但 WCF 資料服務執行階段絕不會分析，或傳回 cookie。 WCF Data Services 用戶端程式庫也不會處理在回應中傳送的 cookie。  
  
### <a name="custom-hosting-requirements"></a>自訂裝載需求  
 根據預設，WCF Data Services 會建立為在 IIS 中裝載的 ASP.NET 應用程式。 這可讓資料服務運用此平台的安全行為。 您可以定義由自訂主機所裝載的 WCF Data Services。 如需詳細資訊，請參閱 <<c0> [ 裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)。 裝載資料服務的元件和平台必須確定下列安全性行為，以防止資料服務的攻擊：  
  
- 限制所有可能作業之資料服務要求中接受的 URI 長度。  
  
- 限制傳入與傳出之 HTTP 訊息的大小。  
  
- 限制在任何指定時間的未完成要求總數。  
  
- 限制 HTTP 標頭和其值的大小，並提供 WCF 資料服務存取標頭的資料。  
  
- 偵測並還擊已知的攻擊，如 TCP SYN 和訊息重新執行攻擊。  
  
### <a name="values-are-not-further-encoded"></a>值不會進一步編碼  
 傳送至資料服務的屬性值不會進一步編碼由 WCF Data Services 的執行階段。 例如，當實體的字串屬性包含 HTML 格式的內容時，資料服務不會以 HTML 編碼標記。 資料服務也不會進一步編碼回應中的屬性值。 用戶端程式庫也不會執行任何額外的編碼。  
  
### <a name="considerations-for-client-applications"></a>用戶端應用程式的考量  
 下列安全性考量適用於使用 WCF Data Services 用戶端來存取 OData 服務的應用程式：  
  
- 用戶端程式庫假設用來存取資料服務的通訊協定會提供適當的安全性層級。  
  
- 用戶端程式庫會針對基礎平台提供之傳輸堆疊的逾時和剖析選項，使用所有預設值。  
  
- 用戶端程式庫不會從應用程式組態檔讀取任何設定。  
  
- 用戶端程式庫不會實作任何跨網域存取機制。 但是，它會依賴基礎 HTTP 堆疊所提供的機制。  
  
- 用戶端程式庫沒有使用者介面項目，因此，絕不會嘗試顯示或呈現它所接收或傳送的資料。  
  
- 建議用戶端應用程式一律驗證使用者輸入，以及接受自不受信任之服務的資料。  
  
## <a name="see-also"></a>另請參閱

- [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
