---
title: HOW TO：將 Windows Forms 上的物件分層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 6000adeffcc991557e046461f93fec24e1262f54
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651679"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>HOW TO：將 Windows Forms 上的物件分層
當您建立複雜的使用者介面，或使用多個文件介面 (MDI) 表單時，您通常要控制項和子表單，以建立更複雜的使用者介面 (UI) 層級。 移動和追蹤的控制項和 windows 群組的內容中，您可以使用他們的疊置順序。 *疊置順序*是沿著表單的 z 軸 （深度） 的表單上控制項的視覺分層。 在頂端的疊置順序的視窗重疊所有其他視窗。 所有其他視窗重疊視窗底部的疊置順序。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-layer-controls-at-design-time"></a>在設計階段的圖層控制項  
  
1. 選取您想要圖層的控制項。  
  
2. 上**格式**功能表上，指向**順序**，然後按一下**提到最上層**或是**移到最下層**。  
  
### <a name="to-layer-controls-programmatically"></a>若要以程式設計方式配置控制項  
  
- 使用<xref:System.Windows.Forms.Control.BringToFront%2A>和<xref:System.Windows.Forms.Control.SendToBack%2A>來操作控制項疊置順序的方法。  
  
     例如，如果<xref:System.Windows.Forms.TextBox>控制項， `txtFirstName`，是下面另一個控制項，而且您想要將它在最上層，請使用下列程式碼：  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Form 支援*控制項內含項目*。 控制項內含項目牽涉到將多個控制項內包含的控制項，例如數目<xref:System.Windows.Forms.RadioButton>控制項內<xref:System.Windows.Forms.GroupBox>控制項。 然後，您可以層中包含的控制項的控制項。 移動 [群組] 中移動了控制項，因為它們包含在其中。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [排列 Windows Forms 上的控制項](arranging-controls-on-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
