---
title: 參數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760232"
---
# <a name="parameters-entity-sql"></a>參數 (Entity SQL)
參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。 每一個參數都有一個名稱和型別， 參數名稱會定義在查詢運算式中使用在 (@) 符號當做前置詞。 這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。  
  
 主應用程式語言的繫結 API 會提供用來繫結參數的 API。  
  
## <a name="example"></a>範例  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
