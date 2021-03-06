---
title: 逐步解說：實作使用背景作業的表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 1988ebd8c5f46346babe212962b617d30d765385
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211538"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>逐步解說：實作使用背景作業的表單

如果您有會花費很長的時間才能完成，且不想您的使用者介面 (UI) 停止回應或 「 擱置 」，您可以使用<xref:System.ComponentModel.BackgroundWorker>類別，以另一個執行緒上執行作業。

此逐步解說將說明如何使用<xref:System.ComponentModel.BackgroundWorker>類別執行耗費時間的計算，「 在背景中 」 時的使用者介面仍然能夠保持回應。  當您進行逐步解說時，您必須讓應用程式以非同步方式計算 Fibonacci 數字。 即使計算大量 Fibonacci 數字需要很長一段時間，主要 UI 執行緒不會受到此延遲的中斷，表單在計算期間仍然有回應。

這個逐步解說中所述的工作包括：

- 建立以 Windows 為基礎的應用程式

- 建立<xref:System.ComponentModel.BackgroundWorker>在表單中

- 新增非同步事件處理常式

- 新增進度報告和支援取消作業

如需在此範例中使用的程式碼的完整清單，請參閱[How to:實作使用背景作業的表單](how-to-implement-a-form-that-uses-a-background-operation.md)。

## <a name="create-a-form-that-uses-a-background-operation"></a>建立使用背景作業的表單

1. 在 Visual Studio 中建立名為以 Windows 為基礎的應用程式專案`BackgroundWorkerExample`(**檔案** > **新增** > **專案** > **視覺化C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 [Form1]，然後從捷徑功能表選取 [重新命名]。 將檔案名稱變更為 `FibonacciCalculator`。 當系統詢問您是否要重新命名程式碼元素 '`Form1`' 的所有參考時，按一下 [是]按鈕。

3. 拖曳<xref:System.Windows.Forms.NumericUpDown>控制項從**工具箱**拖曳至表單。 設定<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>屬性，以`1`並<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>屬性設`91`。

4. 新增兩個<xref:System.Windows.Forms.Button>控制項加入表單。

5. 重新命名第一個<xref:System.Windows.Forms.Button>控制`startAsyncButton`並設定<xref:System.Windows.Forms.Control.Text%2A>屬性設`Start Async`。 重新命名第二個<xref:System.Windows.Forms.Button>控制`cancelAsyncButton`，並將<xref:System.Windows.Forms.Control.Text%2A>屬性設`Cancel Async`。 設定其<xref:System.Windows.Forms.Control.Enabled%2A>屬性設`false`。

6. 這兩個建立的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。 如需詳細資訊，請參閱[如何：建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。

7. 拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單，並重新命名`resultLabel`。

8. 拖曳<xref:System.Windows.Forms.ProgressBar>控制項從**工具箱**拖曳至表單。

## <a name="create-a-backgroundworker-with-the-designer"></a>使用設計工具建立 BackgroundWorker

您可以建立<xref:System.ComponentModel.BackgroundWorker>非同步作業使用**Windows** **Form 設計工具**。

從**元件**索引標籤**工具箱**，拖曳<xref:System.ComponentModel.BackgroundWorker>拖曳至表單。

## <a name="add-asynchronous-event-handlers"></a>新增非同步事件處理常式

您現在已準備好新增事件處理常式<xref:System.ComponentModel.BackgroundWorker>元件的非同步事件。 將會在背景執行的耗費時間作業 (計算 Fibonacci 數字)，會由其中一個事件處理常式呼叫。

1. 在 [**屬性**] 視窗中，使用<xref:System.ComponentModel.BackgroundWorker>元件保持選取，按一下 [**事件**] 按鈕。 按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。 如需如何使用事件處理常式的詳細資訊，請參閱[How to:建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。

2. 在表單中，建立名為 `ComputeFibonacci` 的新方法。 這個方法會執行實際的工作，並且會在背景執行。 此程式碼會示範 Fibonacci 演算法的遞迴實作，它非常沒有效率，對於較大的數字要耗費更長的時間才能完成。 它在這裡是針對說明目的使用，以示範會導致應用程式長時間延遲的作業。

     [!code-cpp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]

3. 在 <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式，將呼叫加入`ComputeFibonacci`方法。 採取的第一個參數`ComputeFibonacci`從<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。 <xref:System.ComponentModel.BackgroundWorker>和<xref:System.ComponentModel.DoWorkEventArgs>參數將稍後用於進度報告與取消支援。 將指定的傳回值`ComputeFibonacci`要<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。 這個結果可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。

    > [!NOTE]
    > <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式不會參考`backgroundWorker1`執行直接個體變數，因為這會結合此事件處理常式的特定執行個體<xref:System.ComponentModel.BackgroundWorker>。 相反地，參考<xref:System.ComponentModel.BackgroundWorker>，會引發這個事件從復原`sender`參數。 當表單裝載一個以上時，這點很重要<xref:System.ComponentModel.BackgroundWorker>。 務必也沒有任何使用者介面中操作物件您<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。 相反地，透過使用者介面通訊<xref:System.ComponentModel.BackgroundWorker>事件。

     [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]

4. 在 `startAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，將會啟動非同步作業的程式碼。

     [!code-cpp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]

5. 在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式，指派的計算結果`resultLabel`控制項。

     [!code-cpp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]

## <a name="adding-progress-reporting-and-support-for-cancellation"></a>新增進度報告和支援取消作業

對於需要長時間的非同步作業，通常會想要對使用者報告進度，並且允許使用者取消作業。 <xref:System.ComponentModel.BackgroundWorker>類別會提供事件，可讓您的背景作業進行時公佈進度。 它也提供旗標，可讓您的背景工作角色程式碼，來偵測呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>並且自行中斷。

### <a name="implement-progress-reporting"></a>實作進度報告

1. 在 [屬性] 視窗中，選取 `backgroundWorker1`。 設定<xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A>並<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性，以`true`。

2. 宣告 `FibonacciCalculator` 表單中的兩個變數。 這些項目會用來追蹤進度。

     [!code-cpp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]

3. 加入 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的事件處理常式。 在 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式中，更新<xref:System.Windows.Forms.ProgressBar>具有<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>屬性<xref:System.ComponentModel.ProgressChangedEventArgs>參數。

     [!code-cpp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]

### <a name="implement-support-for-cancellation"></a>實作支援取消作業

1. 在 `cancelAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，加入程式碼，取消非同步作業。

     [!code-cpp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]

2. `ComputeFibonacci` 方法中的下列程式碼片段會報告進度和支援取消。

     [!code-cpp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]

## <a name="checkpoint"></a>檢查點

此時，您可以編譯並執行 Fibonacci 計算機應用程式。

按下**F5**編譯和執行應用程式。

在背景執行計算時，您會看到<xref:System.Windows.Forms.ProgressBar>顯示計算完成的進度。 您也可以取消暫止的作業。

對於小數字，計算應該非常快速，但是對於較大的數字，您應該會看到明顯的延遲。 如果您輸入的值為 30 或更大，您應該會看到幾秒鐘的延遲，取決於您的電腦速度。 對於大於 40 的值，可能需要數分鐘或數小時才能完成計算。 當計算機忙著計算大量 Fibonacci 數字時，請注意，您可以自由地到處移動表單、最小化、最大化，甚至是關閉表單。 這是因為主要 UI 執行緒並沒有在等待計算完成。

## <a name="next-steps"></a>後續步驟

既然您已實作使用的表單<xref:System.ComponentModel.BackgroundWorker>元件來執行計算，在背景中，您可以探索非同步作業的其他可能性：

- 使用多個<xref:System.ComponentModel.BackgroundWorker>數個同時作業的物件。

- 若要偵錯多執行緒的應用程式，請參閱[How to:使用執行緒視窗](/visualstudio/debugger/how-to-use-the-threads-window)。

- 實作您自己的元件，支援非同步程式設計模型。 如需詳細資訊，請參閱[事件架構非同步模式概觀](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。

    > [!CAUTION]
    > 無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。 請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [受控執行緒處理](../../../standard/threading/index.md)
- [Managed 執行緒處理的最佳實施方針](../../../standard/threading/managed-threading-best-practices.md)
- [事件架構非同步模式概觀](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [如何：實作使用背景作業的表單](how-to-implement-a-form-that-uses-a-background-operation.md)
- [逐步解說：在背景執行作業](walkthrough-running-an-operation-in-the-background.md)
- [BackgroundWorker 元件](backgroundworker-component.md)
