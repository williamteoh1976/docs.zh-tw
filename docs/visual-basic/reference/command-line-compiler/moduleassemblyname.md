---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 70cef109e4f2947fb4e38b9bfd19433257cce136
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663501"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
指定將包含此模組的組件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`assembly_name`|此模組將會是一部分的組件名稱。|  
  
## <a name="remarks"></a>備註  
 編譯器處理序`-moduleassemblyname`選項才`-target:module`已指定選項。 這可讓編譯器建立模組。 編譯器所建立的模組是僅適用於具有指定的組件`-moduleassemblyname`選項。 如果您將模組放在不同的組件時，會發生執行階段錯誤。  
  
 `-moduleassemblyname`只有在下列條件成立時，才需要選項：  
  
- 此模組中的資料類型必須能夠存取`Friend`參考的組件中的型別。  
  
- 參考的組件具有 friend 組件存取權限授與將在其中建置模組的組件。  
  
 如需建立模組的詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。 如需 friend 組件的詳細資訊，請參閱[Friend 組件](../../../standard/assembly/friend-assemblies.md)。  
  
> [!NOTE]
>  `-moduleassemblyname`選項不是從 Visual Studio 開發環境中使用; 它是使用只有當您編譯的命令提示字元。  
  
## <a name="see-also"></a>另請參閱

- [如何：建置多檔案組件](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-參考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Friend 組件](../../../standard/assembly/friend-assemblies.md)
