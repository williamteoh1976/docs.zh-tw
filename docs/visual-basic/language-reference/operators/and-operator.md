---
title: And 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608355"
---
# <a name="and-operator-visual-basic"></a>And 運算子 (Visual Basic)
對兩個執行邏輯結合`Boolean`運算式或兩個數值運算式的位元結合。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值運算式。 布林值相較之下，如`result`是邏輯結合兩個`Boolean`值。 對於位元運算，`result`是數值，代表兩個數值位元模式位元結合。  
  
 `expression1`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression2`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 布林值相較之下，如`result`是`True`並僅有兩個`expression1`並`expression2`評估為`True`。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  布林值相較之下，`And`運算子一律會評估這兩個運算式，這可能包括程序呼叫。 [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)會執行*最少運算*，這表示如果`expression1`是`False`，然後`expression2`不會評估。  
  
 套用至數字的值時`And`運算子會在兩個數值運算式之間執行位元比較相同位置的位元，並對應中位元設`result`根據下表。  
  
|如果位元`expression1`是|在位元和`expression2`是|中的位元`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保正確的結果。  
  
## <a name="data-types"></a>資料類型  
 如果包含運算元`Boolean`Visual Basic 運算式及一個數值運算式，將轉換`Boolean`為數值的運算式 (– 1`True`以 0 代表`False`) 和執行位元運算。  
  
 如需布林值的比較，結果的資料型別是`Boolean`。 如需位元的比較，將結果資料類型是數值類型適合的資料類型`expression1`和`expression2`。 請參閱 < 關聯式和位元比較 」 的表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
> [!NOTE]
>  `And`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`And`運算子執行邏輯結合兩個運算式上。 結果是`Boolean`值，表示兩個運算式是否`True`。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 上述範例產生的結果`True`和`False`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`And`運算子執行邏輯結合的兩個數值運算式的個別位元。 如果運算元的對應位元均設定為 1，則會設定結果模式中的位元。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 上述範例中會分別產生 8，2，0，的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
