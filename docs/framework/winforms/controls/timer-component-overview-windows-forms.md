---
title: Timer 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 5bef0ba87d6a496acf7575965128be2b20b437ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962613"
---
# <a name="timer-component-overview-windows-forms"></a>Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
## <a name="key-properties-methods-and-events"></a>索引鍵屬性、 方法和事件  
 所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值是以毫秒為單位。 啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>就會引發事件在每個間隔。 這是您會在此加入要執行的程式碼。 如需詳細資訊，請參閱[如何：使用 Windows Form Timer 元件集間隔執行程序](run-procedures-at-set-intervals-with-wf-timer-component.md)。 主要方法<xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。 當計時器關閉時，它會重設;沒有任何方法來暫停<xref:System.Windows.Forms.Timer>元件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Timer>
- [Timer 元件](timer-component-windows-forms.md)
- [Windows Forms Timer 元件的 Interval 屬性限制](limitations-of-the-timer-component-interval-property.md)
