---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9a51387cd75d57a6828ecde1dcd788b056f7e27a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766398"
---
# <a name="localissuer"></a>\<localIssuer>
指定要用來取得安全性權杖的本機簽發者位址和繫結。  
  
 \<system.ServiceModel>  
\<behaviors>  
endpointBehaviors 區段  
\<behavior>  
\<clientCredentials>  
\<issuedToken>  
\<localIssuer>  
  
## <a name="syntax"></a>語法  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|位址|必要的字串。 指定本機簽發者的 URI。|  
|繫結|選擇性字串。 系統提供的繫結之一。 如需清單，請參閱[System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。|  
|bindingConfiguration|選擇性字串。 指定組態檔中的繫結組態。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定本機簽發者的身分識別資訊。|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。 您可以使用 `add` 關鍵字將標頭加入這個集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuedToken>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|指定用來向服務驗證用戶端的自訂權杖。|  
  
## <a name="remarks"></a>備註  
 當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。 當<xref:System.ServiceModel.WSFederationHttpBinding>並不提供的 URL 安全性權杖服務，或是聯合繫結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`，用戶端的 Windows Communication Foundation (WCF) 通道會使用所指定的值`address`和`binding`STS，以取得發行的權杖與通訊。 如需有關設定本機簽發者的詳細資訊，請參閱[How to:設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## <a name="example"></a>範例  
 下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [如何：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)
- [如何：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
