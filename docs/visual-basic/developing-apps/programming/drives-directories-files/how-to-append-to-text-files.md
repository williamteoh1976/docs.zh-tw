---
title: 作法：在 Visual Basic 中附加至文字檔
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: e855293ac3636049520a85abdf685091d437bb60
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628912"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>作法：在 Visual Basic 中附加至文字檔
您可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法來附加至文字檔，方法是指定將 `append` 參數設定為 `True`。  
  
### <a name="to-append-to-a-text-file"></a>附加至文字檔  
  
- 使用 `WriteAllText` 方法，並指定要附加的目標檔案和字串以及將 `append` 參數設定為 `True`。  
  
     這個範例會將 `"This is a test string."` 字串寫入名為 `Testfile.txt` 的檔案中。  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- 因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
- 路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
- `File` 指向不存在的路徑 (<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>)。  
  
- 檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。  
  
- 路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
- 路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
- 使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
