---
title: 最佳化效能：資料繫結
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: ac7ca815bedf180c8a680840f585d08f7018d6ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773109"
---
# <a name="optimizing-performance-data-binding"></a>最佳化效能：資料繫結
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。 項目可以和各種資料來源的資料繫結，資料的形式可以是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件和 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]。  
  
 本主題提供資料繫結的效能建議。  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>資料繫結參考的解析方式  
 在討論資料繫結效能問題之前，值得先探討 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結引擎如何解析物件參考以進行繫結。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結的來源可以是任何 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件。 您可以繫結至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的屬性、子屬性或索引子。 繫結參考會解決使用任一 Microsoft.NET Framework 反映或<xref:System.ComponentModel.ICustomTypeDescriptor>。 以下是三種解析繫結用之物件參考的方法。  
  
 第一個方法涉及使用反映。 在此情況下，<xref:System.Reflection.PropertyInfo>物件用來探索屬性的屬性，並提供屬性中繼資料的存取。 當使用<xref:System.ComponentModel.ICustomTypeDescriptor>介面，資料繫結引擎會使用此介面來存取屬性值。 <xref:System.ComponentModel.ICustomTypeDescriptor>介面是在物件與一組靜態屬性沒有的情況下特別有用。  
  
 可提供藉由實作屬性變更通知<xref:System.ComponentModel.INotifyPropertyChanged>介面或使用相關聯的變更通知<xref:System.ComponentModel.TypeDescriptor>。 不過，實作屬性變更通知的慣用的策略是使用<xref:System.ComponentModel.INotifyPropertyChanged>。  
  
 如果來源物件是[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]物件，且來源屬性是[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]資料繫結引擎必須先在來源物件上使用反映來取得<xref:System.ComponentModel.TypeDescriptor>，然後查詢<xref:System.ComponentModel.PropertyDescriptor>。 這個反映作業序列從效能觀點來看可能非常耗時。  
  
 個解析物件參考第二個方法涉及[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]來源物件，可實作<xref:System.ComponentModel.INotifyPropertyChanged>介面，且 [來源] 屬性是[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性。 在此情況下，資料繫結引擎會直接對來源類型使用反映，並取得必要的屬性。 這仍不是最佳的方法，但它的工作集需求的成本會比第一種方法低。  
  
 解析物件參考的第三個方法牽涉到的來源物件<xref:System.Windows.DependencyObject>和 來源屬性<xref:System.Windows.DependencyProperty>。 在此情況下，資料繫結引擎不必使用反映。 相反地，屬性引擎和資料繫結引擎會一起獨立解析屬性參考。 這是解析用於資料繫結之物件參考的最佳方法。  
  
 下表比較的資料繫結的速度<xref:System.Windows.Controls.TextBlock.Text%2A>一千屬性<xref:System.Windows.Controls.TextBlock>使用這三種方法的項目。  
  
|**繫結 TextBlock 的 Text 屬性**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的屬性|115|314|  
|屬性，[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]實作的物件 <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|若要<xref:System.Windows.DependencyProperty>的<xref:System.Windows.DependencyObject>。|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>繫結至大型 CLR 物件  
 當您將資料繫結至單一 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件而它具有數以千計的屬性時，會有顯著的效能影響。 您可以藉由將單一物件分割成多個較少屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件來降低這種影響。 下表顯示單一大型 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件與多個較小物件之資料繫結的繫結和轉譯時間。  
  
|**資料繫結 1000 個 TextBlock 物件**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|至具有 1000 個屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件|950|1200|  
|至 1000 個具有一個屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>繫結至 ItemsSource  
 假設您有[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]<xref:System.Collections.Generic.List%601>物件，包含一份您想要在顯示的員工<xref:System.Windows.Controls.ListBox>。 若要建立這兩個物件之間的對應，您將繫結到員工清單<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.ListBox>。 不過，假設您有新的員工加入您的群組。 您可能會認為，若要將這個新人插入已繫結<xref:System.Windows.Controls.ListBox>值，您只會將這個人加入員工清單，並預期這項變更會自動辨識的資料繫結引擎。 這個假設證明 false;實際上，變更將不會反映在<xref:System.Windows.Controls.ListBox>自動。 這是因為[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]<xref:System.Collections.Generic.List%601>物件不會自動引發集合變更事件。 若要取得<xref:System.Windows.Controls.ListBox>若要挑選所做的變更，您必須重新建立您的員工清單，並將它重新附加<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.ListBox>。 雖然這個解決方案有效，但它造成了嚴重的效能影響。 每次您重新指派<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的<xref:System.Windows.Controls.ListBox>至新的物件，<xref:System.Windows.Controls.ListBox>先棄置之前的項目，並重新產生其整個清單。 效能影響會放大，如果您<xref:System.Windows.Controls.ListBox>對應到複雜的<xref:System.Windows.DataTemplate>。  
  
 這個問題非常有效率的解決方案是對您的員工清單<xref:System.Collections.ObjectModel.ObservableCollection%601>。 <xref:System.Collections.ObjectModel.ObservableCollection%601>物件會引發變更通知資料繫結引擎可接收。 事件會新增或移除項目從<xref:System.Windows.Controls.ItemsControl>而不需要重新產生整個清單。  
  
 下表顯示更新所花費的時間<xref:System.Windows.Controls.ListBox>（具有關閉 UI 虛擬化） 時新增一個項目。 第一個資料列中的數字代表經過時間時[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]<xref:System.Collections.Generic.List%601>物件的繫結至<xref:System.Windows.Controls.ListBox>項目的<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 第二個資料列中的數字代表經過時間時<xref:System.Collections.ObjectModel.ObservableCollection%601>繫結至<xref:System.Windows.Controls.ListBox>項目的<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 請注意很長的時間省下使用<xref:System.Collections.ObjectModel.ObservableCollection%601>資料繫結策略。  
  
|**資料繫結 ItemsSource**|**1 個項目的更新時間 (毫秒)**|  
|--------------------------------------|---------------------------------------|  
|若要[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]<xref:System.Collections.Generic.List%601>物件|1656|  
|若要 <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>將 IList 繫結至 ItemsControl 而非 IEnumerable  
 如果您有繫結之間做選擇<xref:System.Collections.Generic.IList%601>或有<xref:System.Collections.IEnumerable>要<xref:System.Windows.Controls.ItemsControl>物件中，選擇<xref:System.Collections.Generic.IList%601>物件。 繫結<xref:System.Collections.IEnumerable>要<xref:System.Windows.Controls.ItemsControl>強制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]來建立包裝函式<xref:System.Collections.Generic.IList%601>物件，這表示您的效能會受到第二個物件的不必要的額外負荷。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>不要只為了資料繫結而將 CLR 物件轉換成 XML。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您資料繫結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容。不過，資料繫結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容會比資料繫結至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件來得慢。 如果唯一的目的是資料繫結，請不要將 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件轉換成 XML。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [逐步解說：快取中的 WPF 應用程式的應用程式資料](walkthrough-caching-application-data-in-a-wpf-application.md)
