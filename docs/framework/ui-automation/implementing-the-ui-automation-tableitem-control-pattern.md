---
title: 實作 UI 自動化 TableItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3893f69ca6f73665ea3ea4b4f07970b847097f11
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649461"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>實作 UI 自動化 TableItem 控制項模式
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.ITableItemProvider>的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.TableItemPattern> 控制項模式是用以支援實作 <xref:System.Windows.Automation.Provider.ITableProvider> 之容器的子控制項。 個別資料格功能的存取權由 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的必要並行實作提供。 此控制項模式相當於 <xref:System.Windows.Automation.Provider.IGridItemProvider>，差別在於任何實作 <xref:System.Windows.Automation.Provider.ITableItemProvider> 的控制項必須以程式設計方式公開個別資料格與其資料列和資料行資訊之間的關聯性。 如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
  
- 如需相關的格線項目功能，請參閱[實作 UI 自動化 GridItem 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)。  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider 的必要成員  
  
|必要成員|成員類型|注意|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|方法|None|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|方法|None|  
  
 此控制項模式沒有任何相關聯的屬性或事件。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 此控制項模式沒有任何相關聯的例外狀況。  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [實作 UI 自動化 Table 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [實作 UI 自動化 GridItem 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
