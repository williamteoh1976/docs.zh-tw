---
title: HOW TO：ToolBar 上的樣式控制項
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 90ff02747d762b5853a1f60eb99be574503e27f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640834"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>HOW TO：ToolBar 上的樣式控制項
<xref:System.Windows.Controls.ToolBar>定義<xref:System.Windows.ResourceKey>物件，以指定控制項內的樣式<xref:System.Windows.Controls.ToolBar>。  若要設定在控制項的樣式<xref:System.Windows.Controls.ToolBar>，將`x:key`要的樣式屬性<xref:System.Windows.ResourceKey>中定義<xref:System.Windows.Controls.ToolBar>。  
  
 <xref:System.Windows.Controls.ToolBar>定義下列<xref:System.Windows.ResourceKey>物件：  
  
- <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>範例  
 下列範例會定義內的控制項樣式<xref:System.Windows.Controls.ToolBar>。  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](styling-and-templating.md)
