---
title: 工作流程探索範例
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 9a0d3ad22b4663ee71b5b2aa8d0e3d64f20996d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006456"
---
# <a name="workflow-discovery-sample"></a>工作流程探索範例
此範例示範如何讓工作流程服務可以探索，以及如何撰寫可搜尋特定服務的自訂程式碼活動。  
  
## <a name="demonstrates"></a>示範  
 探索尋找活動與工作流程使用方式  
  
## <a name="discussion"></a>討論  
 在此範例的第一個部分中，工作流程服務可以使用組態變成可搜尋的。 組態也可以用來正確套用具有自訂中繼資料 (如範圍) 的服務。 在用戶端上，此範例會使用自訂程式碼活動，這個活動會使用探索來搜尋符合特定合約的服務。 程式碼活動會輸出一個稍後由傳送活動使用的 URI。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 這個範例會使用 HTTP 端點，必須執行正確的 URL Acl (請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)。 以更高的命令提示字元執行下列命令應該就能加入適當的 ACL。 如果您的 Shell 不了解變數格式，請將 Domain 和 Username 替換成下列引數。  
  
     **netsh http add urlacl =http://+:8000/使用者 = %網域 %\\%username%**  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
