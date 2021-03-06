---
title: 支援的部署案例： WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: f1a95e5448d2cc8f1ac472c3b1735f58460e2be6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639144"
---
# <a name="supported-deployment-scenarios"></a>支援的部署案例

支援在部分信任應用程式中使用的 Windows Communication Foundation (WCF) 功能子集主要被為了符合需求的部分，而不是全部使用 WCF 的案例。 在伺服器上，WCF 符合網際網路範圍的要求會共用主控提供者執行第三方應用程式中[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]度信任權限的安全性考量。 在用戶端，WCF 部分信任支援主要為了符合的部署技術需求這類[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的允許無接縫且安全的 XAML 瀏覽器應用程式技術從受信任的站台的桌面應用程式的部署。

## <a name="minimum-permission-requirements"></a>最小權限需求

WCF 中其中一個下列標準具名權限集下執行應用程式支援功能的子集：

- 中度信任權限

- 網際網路區域權限

嘗試在具有更嚴格的權限的部分信任應用程式中使用 WCF，可能會導致在執行階段的安全性例外狀況。

如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。

## <a name="partial-trust-on-the-server"></a>在伺服器上的部分信任

許多 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式裝載服務的商業提供者要求，在他們的伺服器上執行的應用程式必須透過 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 中度信任使用權限集合來執行。 前提是他們所使用，WCF 服務可以在這些環境中執行<xref:System.ServiceModel.BasicHttpBinding>，則<xref:System.ServiceModel.WebHttpBinding>，或<xref:System.ServiceModel.WSHttpBinding>具有傳輸層級安全性。

在中度信任裝載環境執行的 WCF 服務也可以藉由將訊息傳送至用戶端要求的回應中的其他伺服器做為中介層服務。 如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。

除了 SOAP 訊息使用其中一個支援的 SOAP 繫結，WCF 還支援<xref:System.ServiceModel.WebHttpBinding>建置部分信任的應用程式中的 Web 樣式服務。 [WCF Web HTTP 程式設計模型](wcf-web-http-programming-model.md)， [WCF 新聞訂閱](wcf-syndication.md)，並[AJAX 整合與 JSON 支援](ajax-integration-and-json-support.md)WCF 的功能支援在部分信任中。

工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。

如需詳細資訊，請參閱[如何：Use Medium Trust in ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603)。

## <a name="partial-trust-on-the-client"></a>在用戶端上的部分信任

在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) (英文) 和 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式 (XBAP) 技術兩者都會透過部分信任將有限的使用權限 (網際網路區域) 授與不受信任的程式碼。

WCF 可以用來與從部分信任的應用程式透過下列方式部署的遠端伺服器通訊[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或 XBAP。 網際網路區域權限集合包含<xref:System.Net.WebPermission>來源的主機，以允許這些應用程式使用任何支援中所述的 WCF 繫結與其來源伺服器與通訊[Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>另請參閱

- [程式碼存取安全性](../../misc/code-access-security.md)
- [Windows Presentation Foundation 瀏覽器裝載的應用程式概觀](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [部分信任](partial-trust.md)
- [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
