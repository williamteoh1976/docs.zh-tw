---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774133"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>現在，當 .NET 無法處理憑證時，X509Certificate2.ToString(Boolean) 不會擲回例外狀況

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5.2 和更早版本中，如果將 <code>true</code> 傳遞給詳細資訊參數，但 .NET Framework 不支援已安裝的憑證時，此方法會擲回例外狀況。 現在，此方法會成功，並傳回省略無法存取之憑證部分的有效字串。|
|建議|您應該更新所有相依於 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> 的程式碼，以確保傳回字串可在 API 先前擲回例外狀況的特定情況下排除某些憑證資料 (例如公開金鑰、私密金鑰和延伸內容)。|
|範圍|Edge|
|版本|4.6|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
