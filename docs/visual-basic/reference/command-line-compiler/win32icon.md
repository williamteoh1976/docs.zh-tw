---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593093"
---
# <a name="-win32icon"></a>-win32icon
將.ico 檔插入輸出檔。 這個.ico 檔表示中的輸出檔**檔案總管**。  
  
## <a name="syntax"></a>語法  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|要加入至輸出檔的.ico 檔案。 將檔案名稱括在引號 ("") 如果它包含空格。|  
  
## <a name="remarks"></a>備註  
 您可以建立與 Microsoft Windows 資源編譯器 (RC) 的.ico 檔案。 資源編譯器會叫用，當您編譯視覺效果C++程式;.ico 檔是從.rc 檔案建立。 `-win32icon`和`-win32resource`選項互斥。  
  
 請參閱[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考.NET Framework 資源檔，或[-資源 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加.NET Framework 資源檔。 請參閱[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)匯入.res 檔案。  
  
|若要設定-win32icon Visual Studio IDE 中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [應用程式]  索引標籤。<br />3.修改中的值**圖示** 方塊中。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯`In.vb`並附加.ico 檔， `Rf.ico`。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
