---
title: 可多載的運算子 - C# 程式設計指南
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: 850b10958446193026506418c57d7f565c98b714
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452777"
---
# <a name="overloadable-operators-c-programming-guide"></a>可多載的運算子 (C# 程式設計手冊)

C# 允許使用者定義的類型使用 [operator](../../language-reference/keywords/operator.md) 關鍵字來定義靜態成員函式，以多載運算子。 不過，並非所有運算子都可以多載，其他運算子有限制，如本表所示：

| 運算子 | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md)、[-](../../language-reference/operators/subtraction-operator.md)、[!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)、[~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++](../../language-reference/operators/arithmetic-operators.md#increment-operator-)、[--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/keywords/true-false-operators.md)、[false](../../language-reference/keywords/true-false-operators.md)|可多載這些一元運算子。|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|可多載這些二元運算子。|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/comparison-operators.md#less-than-operator-), [>](../../language-reference/operators/comparison-operators.md#greater-than-operator-), [\<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-), [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-)|可多載比較運算子 (但請參閱本表後面的注意事項)。|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|條件式邏輯運算子無法多載，但它們可以使用可多載的 `&` 和 <code>&#124;</code> 評估。|
|[&#91;&#93;](../../language-reference/operators/member-access-operators.md#indexer-operator-)|陣列索引運算子無法多載，但您可以定義[索引子](../indexers/index.md)。|
|[(T)x](../../language-reference/operators/invocation-operator.md)|雖然轉換運算子無法多載，但您可以定義新的轉換運算子 (請參閱[明確](../../language-reference/keywords/explicit.md)和[隱含](../../language-reference/keywords/implicit.md))。|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|無法明確多載指派運算子。 不過，當您多載二元運算子時，對應的指派運算子 (若有) 也會隱含地多載。 例如，`+=` 是使用 `+` 進行評估 (可多載)。|
|[=](../../language-reference/operators/assignment-operator.md)、[.](../../language-reference/operators/member-access-operators.md#member-access-operator-)、[?:](../../language-reference/operators/conditional-operator.md)、[??](../../language-reference/operators/null-coalescing-operator.md)、[->](../../language-reference/operators/dereference-operator.md)、[=>](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/member-access-operators.md#invocation-operator-)、[as](../../language-reference/keywords/as.md)、[checked](../../language-reference/keywords/checked.md)、[unchecked](../../language-reference/keywords/unchecked.md)、[default](../../programming-guide/statements-expressions-operators/default-value-expressions.md)、[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md)、[is](../../language-reference/keywords/is.md)、[new](../../language-reference/keywords/new.md)、[sizeof](../../language-reference/keywords/sizeof.md)[typeof](../../language-reference/keywords/typeof.md)|這些運算子無法多載。|

> [!NOTE]
> 若要多載比較運算子，則必須成對多載；也就是說，如果多載 `==`，也必須多載 `!=`。 反向也是如此，其中多載 `!=` 需要多載 `==`。 比較運算子 `<` 和 `>` 以及 `<=` 和 `>=` 也是如此。

如需如何多載運算子的資訊，請參閱 [operator](../../language-reference/keywords/operator.md) 關鍵字文章。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [陳述式、運算式和運算子](index.md)
- [運算子](operators.md)
- [C# 運算子](../../language-reference/operators/index.md)
- [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/) (為什麼多載運算子在 C# 中一律為靜態？)
