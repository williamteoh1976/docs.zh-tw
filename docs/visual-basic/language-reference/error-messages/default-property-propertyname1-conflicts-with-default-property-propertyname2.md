---
title: 預設屬性 '<propertyname1>' 與基底 '<propertyname2>' 中的預設屬性 '<classname>' 產生衝突，所以必須宣告為 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: c964003217e7b96cf25288e2ae6ae6a2fb07a6c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651383"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>預設屬性 '\<屬性名稱 1&gt >' 衝突的預設屬性'\<propertyname2 >' 中 '\<類別名稱 >'，所以應宣告為 'Shadows'
屬性會宣告具有相同名稱做為基底類別中定義的屬性。 在此情況下，此類別中的屬性應該會遮蔽基底類別屬性。  
  
 這個訊息是一個警告。 預設會假設為`Shadows` 。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。  
  
## <a name="see-also"></a>另請參閱

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
