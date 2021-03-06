---
title: 作法：建立適用於資料輸入且可調整大小的 Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 1b27c0e67aae1935c4216654d9f3ddf557719572
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588934"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>作法：建立適用於資料輸入且可調整大小的 Windows Forms
良好的配置會適當回應在父表單維度中的變更。 您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來排列表單的配置，以和表單維度變更一致的方式調整控制項大小及置放控制項。 當控制項內容中的變更造成配置變更時，<xref:System.Windows.Forms.TableLayoutPanel> 控制項也很有用。 這個程序所涵蓋的流程可在 Visual Studio 環境中完成。  另請參閱[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建置在使用者調整表單大小時會適當回應的配置。 它也會示範可適當回應當地語系化的配置。  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [如何：設計可適當回應當地語系化的 Windows Forms 配置](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。Redmond，WA:Microsoft Press，1999年。(USBN:0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
