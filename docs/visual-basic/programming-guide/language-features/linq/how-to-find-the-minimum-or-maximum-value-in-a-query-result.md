---
title: HOW TO：查詢結果中尋找最小值或最大值，使用 LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: af5f4bf829664057c40004a842df95d927cc5d71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337470"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>HOW TO：查詢結果中尋找最小值或最大值，使用 LINQ (Visual Basic)
Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。  
  
 下列範例示範如何建立新的應用程式會執行對 SQL Server 資料庫的查詢。 此範例使用決定結果的最小和最大值`Aggregate`和`Group By`子句。 如需詳細資訊，請參閱 <<c0> [ 彙總子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)並[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。 如需相關指示，請參閱 <<c0> [ 下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1. 在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫檔案總管**上**檢視**功能表。  
  
2. 以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。  
  
3. 請指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要將專案加入包含 LINQ to SQL 檔案  
  
1. 在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。 選取 Visual Basic **Windows Forms 應用程式**作為專案類型。  
  
2. 在 [專案]  功能表中，按一下 [加入新項目] 。 選取  **LINQ to SQL 類別**項目範本。  
  
3. 將檔案命名為 `northwind.dbml`。 按一下 [加入] 。 Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>若要將資料表加入至查詢至 O/R 設計工具  
  
1. 在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 依序展開**資料表**資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2. 按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。 按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。  
  
     設計工具建立新`Customer`和`Order`物件，為您的專案。 請注意，設計工具會自動偵測資料表之間的關聯性並建立的子系相關物件的屬性。 例如，IntelliSense 會顯示`Customer`物件具有`Orders`該客戶所有訂單的屬性相關。  
  
3. 儲存變更並關閉設計工具。  
  
4. 儲存您的專案。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>加入程式碼來查詢資料庫，並顯示結果  
  
1. 從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。  
  
2. 按兩下 Form1 以將程式碼加入`Load`形式的事件。  
  
3. 當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。 此物件包含的程式碼，您必須存取這些資料表，除了個別的物件和每個資料表的集合。 <xref:System.Data.Linq.DataContext>物件您專案的名稱為根據的.dbml 檔案的名稱。 此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>資料表指定 O/R 設計工具在您的程式碼和查詢。  
  
     將下列程式碼加入`Load`事件。 此程式碼會查詢公開為資料內容的屬性，並決定結果的最小和最大值的資料表。 此範例會使用他`Aggregate`子句，以單一的結果，查詢和`Group By`子句，以顯示平均值分組結果。  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. 按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法 (O/R 設計工具)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
