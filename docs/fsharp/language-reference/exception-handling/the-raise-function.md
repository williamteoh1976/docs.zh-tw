---
title: 例外狀況：raise 函式
description: 了解如何F#'raise' 函式用來表示已發生錯誤或例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: 9e2515ad7b85c1025bc3aa0aa2a6929a8d35436d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641956"
---
# <a name="exceptions-the-raise-function"></a>例外狀況：raise 函式

`raise`函式用來表示已發生錯誤或例外狀況。 例外狀況物件中擷取錯誤的相關資訊。

## <a name="syntax"></a>語法

```fsharp
raise (expression)
```

## <a name="remarks"></a>備註

`raise`函式會產生例外狀況物件，並起始堆疊回溯程序。 在堆疊回溯程序被受 common language runtime (CLR)，使此程序的行為都相同，因為它是以任何其他.NET 語言。 在堆疊回溯程序會搜尋符合產生的例外狀況的例外狀況處理常式。 開始在目前的搜尋`try...with`運算式，如果有的話。 在每個模式`with`勾選區塊，順序。 找到相符的例外狀況處理常式時，例外狀況會視為處理;否則，回溯堆疊時和`with`會檢查呼叫鏈結的區塊，直到找到相符的處理常式。 任何`finally`於堆疊回溯呼叫鏈結中發生的區塊也會依序執行。

`raise`函式相當於`throw`在C#或C++。 使用`reraise`catch 處理常式傳播相同的例外狀況呼叫鏈結中。

下列程式碼範例說明使用`raise`函式來產生例外狀況。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise`函式也可用來引發.NET 例外狀況，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...with`運算式](the-try-with-expression.md)
- [例外狀況：`try...finally`運算式](the-try-finally-expression.md)
- [例外狀況：`failwith`函式](the-failwith-function.md)
- [例外狀況：`invalidArg`函式](the-invalidArg-function.md)
