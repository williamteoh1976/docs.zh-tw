---
title: HOW TO：列出資料物件中的資料格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001490"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>HOW TO：列出資料物件中的資料格式
下列範例示範如何使用<xref:System.Windows.DataObject.GetFormats%2A>方法多載取得用以表示使用資料物件中每個資料格式的字串陣列。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示資料物件 （原生和自動轉換） 中可用的所有資料格式的字串陣列。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示只有可用的資料格式的資料物件 （自動轉換的資料格式會進行篩選） 中的字串陣列。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.IDataObject>
- [拖放概觀](drag-and-drop-overview.md)
