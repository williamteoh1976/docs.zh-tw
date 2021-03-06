---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: ff4b1729f1b9fb1d698b4b5b1e3711ce3d27b4db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639031"
---
# <a name="-rootnamespace"></a>-rootnamespace
指定所有類型宣告的命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespace`|在用來括住目前專案的所有類型宣告的命名空間名稱。|  
  
## <a name="remarks"></a>備註  
 如果您使用 Visual Studio 可執行檔 (Devenv.exe) 編譯所建立的專案在 Visual Studio 整合式的開發環境，請使用`-rootnamespace`指定的值<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>屬性。 請參閱[Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)如需詳細資訊。  
  
 使用 common language runtime MSIL 反組譯 (`Ildasm.exe`) 若要檢視輸出檔案中的命名空間名稱。  
  
|若要在 Visual Studio 整合式的開發環境中設定-rootnamespace|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [應用程式]  索引標籤。<br />3.修改中的值**根命名空間** 方塊中。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯`In.vb`而命名空間中含括所有類型宣告`mynamespace`。  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (IL 反組譯工具)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
