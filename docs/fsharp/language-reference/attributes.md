---
title: 屬性
description: 了解如何F#屬性可讓要套用至程式設計建構的中繼資料。
ms.date: 05/16/2016
ms.openlocfilehash: fed4c549b95d6d3701ab81cf5d62add411c16038
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642031"
---
# <a name="attributes"></a>屬性

屬性會啟用要套用至程式設計建構的中繼資料。

## <a name="syntax"></a>語法

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>備註

在先前的語法*目標*是選擇性，而且如果有的話，指定的屬性會套用至程式實體類型。 有效值*目標*資料表出現在本文件稍後所示。

*屬性名稱*是指的是有效的屬性型別，不論後置詞的 （可能是完整命名空間） 的名稱`Attribute`，通常會用於屬性型別名稱。 例如，型別`ObsoleteAttribute`可以縮短到`Obsolete`在此內容中。

*引數*是屬性型別的建構函式的引數。 如果屬性有預設建構函式，就可以省略引數清單和括號。 屬性支援位置引數和具名引數。 *位置引數*是以其出現的順序中使用的引數。 如果屬性有公用屬性，則可以使用具名引數。 您可以設定這些引數清單中使用下列語法。

```
*property-name* = *property-value*
```

這類屬性的初始化可以依任何順序，但它們必須遵守任何位置的引數。 以下是使用位置引數和屬性的初始化屬性的範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

在此範例中，屬性是`DllImportAttribute`，這裡用於縮短格式。 第一個引數是位置參數和第二個是屬性。

屬性是.NET 的程式設計建構，可讓物件稱為*屬性*與類型或其他程式項目相關聯。 要套用屬性的程式項目就所謂*屬性目標*。 屬性通常會包含其目標的相關中繼資料。 在此情況下，中繼資料可能是其欄位和成員以外的類型有關的任何資料。

中的屬性F#可以套用到下列的程式設計建構： 函式、 方法、 組件、 模組、 類型 （類別、 記錄、 結構、 介面、 委派、 列舉、 等位和等等）、 建構函式、 屬性、 欄位，參數型別參數，並傳回值。 屬性不允許在`let`類別、 運算式或工作流程運算式內的繫結。

通常，屬性宣告會出現之前將屬性目標的宣告。 可以使用多個屬性宣告，共同作業，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

您可以使用.NET 反映，在執行階段查詢屬性。

您可以個別宣告多個屬性，如同先前的程式碼範例中，或者您可以宣告它們在一組方括號中如果您使用分號來分隔個別的屬性和建構函式，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

通常發生這些屬性包括`Obsolete`COM 支援、 擁有權的程式碼中，與相關的屬性和屬性，指出是否可以序列化的型別屬性的屬性，如需安全性考量的屬性。 下列範例示範如何使用`Obsolete`屬性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

屬性目標`assembly`並`module`，您將屬性套用至最上層`do`繫結組件中。 您可以包含單字`assembly`或`module`在屬性宣告中，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

如果您省略套用至屬性的屬性目標`do`繫結，F#編譯器會嘗試判斷適合該屬性的屬性目標。 許多屬性的類別有類型的屬性`System.AttributeUsageAttribute`包含支援該屬性的可能目標的相關資訊。 如果`System.AttributeUsageAttribute`表示屬性支援做為目標的函式，屬性會套用至程式的主要進入點。 如果`System.AttributeUsageAttribute`表示屬性支援做為目標的組件，編譯器會採用要套用至組件的屬性。 大部分屬性不會套用至函式和組件，但在其中的情況下，屬性會套用至程式的 main 函式。 如果明確指定屬性目標，則會將屬性套用至指定的目標。

雖然您通常不需要指定屬性目標明確的有效值*目標*屬性中會顯示在下列資料表中，以及使用方式的範例。

<table>
  <tr>
    <th>屬性目標</td>
    <th>範例</td> 
  </tr>
  <tr>
    <td>組件</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td>Field - 欄位</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td>屬性</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
  </tr>
  <tr>
    <td>類型</td>
    <td>
        <pre lang="fsharp"><code>
        [&lt;type: StructLayout(Sequential)&gt;] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
