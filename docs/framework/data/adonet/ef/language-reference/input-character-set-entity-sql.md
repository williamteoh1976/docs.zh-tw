---
title: 輸入字元集 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 3795660cf6086aa67596f31e49c4d950aa653d86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780415"
---
# <a name="input-character-set-entity-sql"></a>輸入字元集 (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 接受以 UTF-16 編碼的 UNICODE 字元。  
  
 字串常值 (String Literal) 可包含以單引號括住的任何 UTF-16 字元。 例如，N'文字列リテラル'。 當比較字串常值時，會使用原始的 UTF-16 值。 例如，N'ABC' 在日文字碼頁和拉丁文字碼頁中是不同的。  
  
 註解可包含任何 UTF-16 字元。  
  
 逸出的識別碼可包含以方括弧括住的任何 UTF-16 字元。 例如，[エスケープされた識別子]。 UTF-16 逸出識別碼的比較是不區分大小寫的。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。 例如，如果對應的字元來自相同的字碼頁，則 [ABC] 相當於 [abc]。 然而，如果相同的兩個識別碼來自不同的字碼頁，則不相等。  
  
 空白區是任何 UTF-16 空白字元。  
  
 新行 (Newline) 是任何標準化的 UTF-16 新行字元。 例如，'\n' 和 '\r\n' 會視為新行字元，但是 '\r' 不是新行字元。  
  
 關鍵字、運算式和標點符號可以是任何標準化成拉丁文的 UTF-16 字元。 例如，SELECT 在日文字碼頁中是一個有效的關鍵字。  
  
 關鍵字、運算式和標點符號只能是拉丁文字元。 `SELECT` 在日文字碼頁中不是關鍵字。 +，-， \*、 /、 =、 （、）、 '，[、] 這裡不加引號的任何其他語言建構只能是拉丁字元。  
  
 簡單識別碼只能是拉丁字元。 如此可避免比較期間的模稜兩可 (Ambiguity)，因為會比較原始值。 例如，ABC 會在日文和拉丁文字碼頁不同。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
