---
title: HOW TO：使用影像材質填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781273"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>HOW TO：使用影像材質填滿形狀
您可以使用一個封閉的形狀填滿滿材質<xref:System.Drawing.Image>類別和<xref:System.Drawing.TextureBrush>類別。  
  
## <a name="example"></a>範例  
 下列範例會填滿橢圓形的映像。 程式碼會建構<xref:System.Drawing.Image>物件，並接著會將該位址傳遞<xref:System.Drawing.Image>物件做為引數<xref:System.Drawing.TextureBrush.%23ctor%2A>建構函式。 第三個陳述式會調整映像，以及第四個陳述式填滿橢圓形的縮放的影像的重複複本。  
  
 下列程式碼，<xref:System.Drawing.TextureBrush.Transform%2A>屬性包含它繪製前套用至映像的轉換。 假設原始的映像有 640 像素的寬度和高度 480 像素。 轉換將影像縮小為 75 × 75 藉由設定水平和垂直縮放值。  
  
> [!NOTE]
>  在下列範例中，將映像大小為 75 × 75，而且橢圓形的大小為 150 x 250。 因為映像是小於它正在填滿的橢圓形，橢圓形會並排顯示與映像。 並排影像會水平和垂直重複直到圖形的界限的方法為止。 如需並排顯示的詳細資訊，請參閱[How to:並排顯示影像與圖案](how-to-tile-a-shape-with-an-image.md)。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
