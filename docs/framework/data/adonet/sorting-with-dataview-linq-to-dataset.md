---
title: Sortowania z DataView (LINQ do DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ce75aba79af617b7c3b342a25f2ac8f8ab0f672
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="32733-102">Sortowania z DataView (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="32733-102">Sorting with DataView (LINQ to DataSet)</span></span>
<span data-ttu-id="32733-103">Sortowanie danych na podstawie określonych kryteriów, a następnie prezentować danych do klienta za pomocą formantu interfejsu użytkownika jest ważnym aspektem wiązania z danymi.</span><span class="sxs-lookup"><span data-stu-id="32733-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="32733-104"><xref:System.Data.DataView>udostępnia kilka sposobów, aby posortować dane i zwracanie wszystkich wierszy danych uporządkowanych według określonych kryteriów porządkowania.</span><span class="sxs-lookup"><span data-stu-id="32733-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="32733-105">Oprócz jego podstawie ciąg sortowania możliwości, <xref:System.Data.DataView> także pozwala na użycie [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] wyrażenia kryterium sortowania.</span><span class="sxs-lookup"><span data-stu-id="32733-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] expressions for the sorting criteria.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="32733-106">wyrażenia umożliwia bardziej złożone i zaawansowane operacje sortowania niż sortowanie oparte na ciągach.</span><span class="sxs-lookup"><span data-stu-id="32733-106"> expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="32733-107">W tym temacie opisano oba podejścia do sortowania za pomocą <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="32733-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="32733-108">Tworzenie widoku danych z zapytania z sortowaniem informacji</span><span class="sxs-lookup"><span data-stu-id="32733-108">Creating DataView from a Query with Sorting Information</span></span>  
 <span data-ttu-id="32733-109">A <xref:System.Data.DataView> można utworzyć obiektu z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="32733-109">A <xref:System.Data.DataView> object can be created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query.</span></span> <span data-ttu-id="32733-110">Jeśli kwerenda zawiera <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, lub <xref:System.Linq.Enumerable.ThenByDescending%2A> wyrażeń w klauzuli te są używane jako podstawa sortowania danych w klauzuli <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="32733-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="32733-111">Na przykład, jeśli zapytanie zawiera `Order By…`i `Then By…` klauzule powstałe w ten sposób <xref:System.Data.DataView> czy określanie kolejności według obu kolumn określonych danych.</span><span class="sxs-lookup"><span data-stu-id="32733-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="32733-112">Oparte na wyrażeniach sortowania oferuje bardziej zaawansowaną i złożone sortowania niż prostsze oparte na ciąg sortowania.</span><span class="sxs-lookup"><span data-stu-id="32733-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="32733-113">Należy pamiętać, że na podstawie ciągu i oparte na wyrażeniach sortowania wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="32733-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="32733-114">Jeśli ciąg podstawie <xref:System.Data.DataView.Sort%2A> jest ustawiany po <xref:System.Data.DataView> jest tworzony w wyniku zapytania oparte na wyrażeniach filtru wywnioskować na podstawie zapytania jest wyczyszczone i nie można przywrócić.</span><span class="sxs-lookup"><span data-stu-id="32733-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="32733-115">Indeks <xref:System.Data.DataView> składa się zarówno w przypadku <xref:System.Data.DataView> jest tworzony i podczas sortowania i filtrowania informacji jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="32733-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="32733-116">Możesz uzyskać najlepszą wydajność, podając kryteria sortowania w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie <xref:System.Data.DataView> jest tworzona na podstawie i nie modyfikowanie sortowania informacje, a później.</span><span class="sxs-lookup"><span data-stu-id="32733-116">You get the best performance by supplying sorting criteria in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="32733-117">Aby uzyskać więcej informacji, zobacz [wydajności DataView](../../../../docs/framework/data/adonet/dataview-performance.md).</span><span class="sxs-lookup"><span data-stu-id="32733-117">For more information, see [DataView Performance](../../../../docs/framework/data/adonet/dataview-performance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32733-118">W większości przypadków wyrażenia używane do sortowania nie powinny mieć efekty uboczne i musi być deterministyczny.</span><span class="sxs-lookup"><span data-stu-id="32733-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="32733-119">Ponadto wyrażenia nie może zawierać dowolną logikę, która jest zależna od zestawu Liczba wykonań, ponieważ sortowania operacje mogą być wykonywane dowolną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="32733-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="32733-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-120">Example</span></span>  
 <span data-ttu-id="32733-121">W poniższym przykładzie zapytanie tabeli SalesOrderHeader i porządkuje zwrócone wiersze według dat zamówienia; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="32733-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="32733-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-122">Example</span></span>  
 <span data-ttu-id="32733-123">W poniższym przykładzie zapytanie tabeli SalesOrderHeader i porządkuje wiersza zwrócone przez suma. Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="32733-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="32733-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-124">Example</span></span>  
 <span data-ttu-id="32733-125">W poniższym przykładzie zapytanie tabeli Szczegóły zamówienia sprzedaży i porządkuje zwrócone wiersze według ilości zlecenia, a następnie według Identyfikatora zamówienia; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="32733-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="32733-126">Za pomocą właściwości sortowania oparte na ciągach</span><span class="sxs-lookup"><span data-stu-id="32733-126">Using the String-Based Sort Property</span></span>  
 <span data-ttu-id="32733-127">Ciąg sortowania funkcje związane z <xref:System.Data.DataView> nadal działa z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32733-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="32733-128">Po <xref:System.Data.DataView> została utworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kwerendy, można użyć <xref:System.Data.DataView.Sort%2A> właściwość umożliwiająca ustawienie sortowania na <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="32733-128">After a <xref:System.Data.DataView> has been created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="32733-129">Na podstawie ciągu i oparte na wyrażeniach sortowania funkcje wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="32733-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="32733-130">Ustawienie <xref:System.Data.DataView.Sort%2A> właściwość spowoduje wyczyszczenie oparte na wyrażeniach sortowania dziedziczone z poziomu zapytania który <xref:System.Data.DataView> został utworzony na podstawie.</span><span class="sxs-lookup"><span data-stu-id="32733-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="32733-131">Aby uzyskać więcej informacji na temat na podstawie ciągu <xref:System.Data.DataView.Sort%2A> filtrowania, zobacz [sortowanie i filtrowanie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="32733-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="32733-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-132">Example</span></span>  
 <span data-ttu-id="32733-133">W przykładzie poniżej tworzy <xref:System.Data.DataView> z kontaktu tabela i wiersze są sortowane według nazwiska malejąco kolejności, a następnie imię w kolejności rosnącej:</span><span class="sxs-lookup"><span data-stu-id="32733-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="32733-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-134">Example</span></span>  
 <span data-ttu-id="32733-135">Poniższy przykład wysyła zapytanie do tabeli kontaktów nazwiska rozpoczynające się od litery "S".</span><span class="sxs-lookup"><span data-stu-id="32733-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="32733-136">A <xref:System.Data.DataView> jest tworzone na podstawie zapytania i powiązany <xref:System.Windows.Forms.BindingSource> obiektu.</span><span class="sxs-lookup"><span data-stu-id="32733-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="32733-137">Wyczyszczenie sortowania</span><span class="sxs-lookup"><span data-stu-id="32733-137">Clearing the Sort</span></span>  
 <span data-ttu-id="32733-138">Kryteria sortowania na <xref:System.Data.DataView> można wyczyścić po ustawieniu, przy użyciu <xref:System.Data.DataView.Sort%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="32733-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="32733-139">Istnieją dwa sposoby, aby wyczyścić informacje sortowania w <xref:System.Data.DataView>:</span><span class="sxs-lookup"><span data-stu-id="32733-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
-   <span data-ttu-id="32733-140">Ustaw <xref:System.Data.DataView.Sort%2A> właściwości `null`.</span><span class="sxs-lookup"><span data-stu-id="32733-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
-   <span data-ttu-id="32733-141">Ustaw <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="32733-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="32733-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-142">Example</span></span>  
 <span data-ttu-id="32733-143">Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania i czyści sortowanie przez ustawienie <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg:</span><span class="sxs-lookup"><span data-stu-id="32733-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="32733-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="32733-144">Example</span></span>  
 <span data-ttu-id="32733-145">Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt i zestawy <xref:System.Data.DataView.Sort%2A> właściwości, aby posortować według nazwisko w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="32733-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="32733-146">Następnie wyczyścić kryteria sortowania, ustawiając <xref:System.Data.DataView.Sort%2A> właściwości `null`:</span><span class="sxs-lookup"><span data-stu-id="32733-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="32733-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32733-147">See Also</span></span>  
 [<span data-ttu-id="32733-148">Powiązanie danych i LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="32733-148">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [<span data-ttu-id="32733-149">Filtrowanie z widoku danych.</span><span class="sxs-lookup"><span data-stu-id="32733-149">Filtering with DataView</span></span>](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [<span data-ttu-id="32733-150">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="32733-150">Sorting Data</span></span>](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)