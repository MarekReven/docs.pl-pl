---
title: "BlockingCollection — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dc6729bf4627164fbcde5980d4fcccd41b67645
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="blockingcollection-overview"></a><span data-ttu-id="b1e73-102">BlockingCollection — Przegląd</span><span class="sxs-lookup"><span data-stu-id="b1e73-102">BlockingCollection Overview</span></span>
<span data-ttu-id="b1e73-103"><xref:System.Collections.Concurrent.BlockingCollection%601>to klasa wątkowo kolekcji, która zapewnia następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b1e73-103"><xref:System.Collections.Concurrent.BlockingCollection%601> is a thread-safe collection class that provides the following features:</span></span>  
  
-   <span data-ttu-id="b1e73-104">Implementacja wzorca producent — konsument.</span><span class="sxs-lookup"><span data-stu-id="b1e73-104">An implementation of the Producer-Consumer pattern.</span></span>  
  
-   <span data-ttu-id="b1e73-105">Współbieżne Dodawanie i pobieranie elementów z wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="b1e73-105">Concurrent adding and taking of items from multiple threads.</span></span>  
  
-   <span data-ttu-id="b1e73-106">Opcjonalne maksymalnej pojemności.</span><span class="sxs-lookup"><span data-stu-id="b1e73-106">Optional maximum capacity.</span></span>  
  
-   <span data-ttu-id="b1e73-107">W przypadku operacji wstawiania i usuwania, które zablokować, jeśli kolekcja jest pusta lub pełnego.</span><span class="sxs-lookup"><span data-stu-id="b1e73-107">Insertion and removal operations that block when collection is empty or full.</span></span>  
  
-   <span data-ttu-id="b1e73-108">Wstawianie i usuwanie "try" operacje nie należy blokować lub który zablokować maksymalnie w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="b1e73-108">Insertion and removal "try" operations that do not block or that block up to a specified period of time.</span></span>  
  
-   <span data-ttu-id="b1e73-109">Hermetyzuje wszystkie typ kolekcji implementujący<xref:System.Collections.Concurrent.IProducerConsumerCollection%601></span><span class="sxs-lookup"><span data-stu-id="b1e73-109">Encapsulates any collection type that implements <xref:System.Collections.Concurrent.IProducerConsumerCollection%601></span></span>  
  
-   <span data-ttu-id="b1e73-110">Anulowanie z tokenami anulowania.</span><span class="sxs-lookup"><span data-stu-id="b1e73-110">Cancellation with cancellation tokens.</span></span>  
  
-   <span data-ttu-id="b1e73-111">Dwa rodzaje wyliczenie z `foreach` (`For Each` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="b1e73-111">Two kinds of enumeration with `foreach` (`For Each` in Visual Basic):</span></span>  
  
    1.  <span data-ttu-id="b1e73-112">Wyliczenie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b1e73-112">Read-only enumeration.</span></span>  
  
    2.  <span data-ttu-id="b1e73-113">Wyliczenie, które powoduje usunięcie elementów, ponieważ są one wyliczone.</span><span class="sxs-lookup"><span data-stu-id="b1e73-113">Enumeration that removes items as they are enumerated.</span></span>  
  
## <a name="bounding-and-blocking-support"></a><span data-ttu-id="b1e73-114">Obsługa blokujących i ograniczających</span><span class="sxs-lookup"><span data-stu-id="b1e73-114">Bounding and Blocking Support</span></span>  
 <span data-ttu-id="b1e73-115"><xref:System.Collections.Concurrent.BlockingCollection%601>obsługuje blokujących i ograniczających.</span><span class="sxs-lookup"><span data-stu-id="b1e73-115"><xref:System.Collections.Concurrent.BlockingCollection%601> supports bounding and blocking.</span></span> <span data-ttu-id="b1e73-116">Ograniczenia oznacza, że można ustawić maksymalną pojemność kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b1e73-116">Bounding means you can set the maximum capacity of the collection.</span></span> <span data-ttu-id="b1e73-117">Ograniczenia jest ważne w niektórych scenariuszach, ponieważ pozwala kontrolować maksymalny rozmiar kolekcji w pamięci, i uniemożliwia tworzenie wątków przenoszenie zbyt daleko wcześniejsze odbierającą wątków.</span><span class="sxs-lookup"><span data-stu-id="b1e73-117">Bounding is important in certain scenarios because it enables you to control the maximum size of the collection in memory, and it prevents the producing threads from moving too far ahead of the consuming threads.</span></span>  
  
 <span data-ttu-id="b1e73-118">Wiele wątków lub zadań można dodać elementy do kolekcji jednocześnie, a jeśli kolekcji osiągnie określony maksymalną pojemność, Tworzenie wątków zablokuje do momentu usunięcia elementu.</span><span class="sxs-lookup"><span data-stu-id="b1e73-118">Multiple threads or tasks can add items to the collection concurrently, and if the collection reaches its specified maximum capacity, the producing threads will block until an item is removed.</span></span> <span data-ttu-id="b1e73-119">Wielu klientów może jednocześnie usunąć elementy, a jeśli kolekcja jest pusta, odbierającą wątków zablokuje dopóki producent dodaje element.</span><span class="sxs-lookup"><span data-stu-id="b1e73-119">Multiple consumers can remove items concurrently, and if the collection becomes empty, the consuming threads will block until a producer adds an item.</span></span> <span data-ttu-id="b1e73-120">Tworzenie wątków można wywołać <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> aby wskazać, że ma więcej elementów zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="b1e73-120">A producing thread can call <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> to indicate that no more items will be added.</span></span> <span data-ttu-id="b1e73-121">Monitor konsumentów <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość, aby dowiedzieć się, gdy kolekcja jest pusta i ma więcej elementów zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="b1e73-121">Consumers monitor the <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> property to know when the collection is empty and no more items will be added.</span></span> <span data-ttu-id="b1e73-122">W poniższym przykładzie przedstawiono prosty kolekcji BlockingCollection o ograniczonej pojemności 100.</span><span class="sxs-lookup"><span data-stu-id="b1e73-122">The following example shows a simple BlockingCollection with a bounded capacity of 100.</span></span> <span data-ttu-id="b1e73-123">Zadanie producent dodaje elementów do kolekcji, tak długo, jak niektóre zewnętrznych warunek jest spełniony, a następnie wywołuje <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1e73-123">A producer task adds items to the collection as long as some external condition is true, and then calls <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>.</span></span> <span data-ttu-id="b1e73-124">Zadanie konsumenta trwa elementów do <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="b1e73-124">The consumer task takes items until the <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> property is true.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 <span data-ttu-id="b1e73-125">Pełny przykład, zobacz [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-125">For a complete example, see [How to: Add and Take Items Individually from a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span></span>  
  
## <a name="timed-blocking-operations"></a><span data-ttu-id="b1e73-126">Upłynął, blokowanie operacji</span><span class="sxs-lookup"><span data-stu-id="b1e73-126">Timed Blocking Operations</span></span>  
 <span data-ttu-id="b1e73-127">W upłynął blokuje <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji w kolekcjach ograniczonych, metoda próbuje dodać lub podjąć element.</span><span class="sxs-lookup"><span data-stu-id="b1e73-127">In timed blocking <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operations on bounded collections, the method tries to add or take an item.</span></span> <span data-ttu-id="b1e73-128">Jeśli element jest dostępny jest umieszczona w zmiennej, która została przekazana przez odwołanie, a metoda zwraca wartość true.</span><span class="sxs-lookup"><span data-stu-id="b1e73-128">If an item is available it is placed into the variable that was passed in by reference, and the method returns true.</span></span> <span data-ttu-id="b1e73-129">Metoda zwraca wartość false, jeśli żaden element jest pobierany po upływie określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="b1e73-129">If no item is retrieved after a specified time-out period the method returns false.</span></span> <span data-ttu-id="b1e73-130">Wątek jest bezpłatna inne przydatne pracy przed podjęciem ponownej próby można uzyskać dostępu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b1e73-130">The thread is then free to do some other useful work before trying again to access the collection.</span></span> <span data-ttu-id="b1e73-131">Na przykład czasu blokowanie dostępu, zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-131">For an example of timed blocking access, see the second example in [How to: Add and Take Items Individually from a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span></span>  
  
## <a name="cancelling-add-and-take-operations"></a><span data-ttu-id="b1e73-132">Anulowanie Dodaj i podejmij działania</span><span class="sxs-lookup"><span data-stu-id="b1e73-132">Cancelling Add and Take Operations</span></span>  
 <span data-ttu-id="b1e73-133">Dodaj i zazwyczaj wykonywane są operacje podejmuje w pętli.</span><span class="sxs-lookup"><span data-stu-id="b1e73-133">Add and Take operations are typically performed in a loop.</span></span> <span data-ttu-id="b1e73-134">Możesz anulować pętlę przez przekazywanie <xref:System.Threading.CancellationToken> do <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, a następnie zaznaczając wartość tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości w każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="b1e73-134">You can cancel a loop by passing in a <xref:System.Threading.CancellationToken> to the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, and then checking the value of the token's <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property on each iteration.</span></span> <span data-ttu-id="b1e73-135">Jeśli ma wartość true, będzie ona wówczas od użytkownika odpowiada żądanie anulowania przez wyczyszczenie wszystkich zasobów i wyjścia z pętli.</span><span class="sxs-lookup"><span data-stu-id="b1e73-135">If the value is true, then it is up to you to respond the cancellation request by cleaning up any resources and exiting the loop.</span></span> <span data-ttu-id="b1e73-136">W poniższym przykładzie przedstawiono przeciążenia <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> pobierającej anulowania tokenu i kod używający go:</span><span class="sxs-lookup"><span data-stu-id="b1e73-136">The following example shows an overload of <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> that takes a cancellation token, and the code that uses it:</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 <span data-ttu-id="b1e73-137">Na przykład sposobu obsługi anulowania Zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-137">For an example of how to add cancellation support, see the second example in [How to: Add and Take Items Individually from a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).</span></span>  
  
## <a name="specifying-the-collection-type"></a><span data-ttu-id="b1e73-138">Określanie typu kolekcji</span><span class="sxs-lookup"><span data-stu-id="b1e73-138">Specifying the Collection Type</span></span>  
 <span data-ttu-id="b1e73-139">Po utworzeniu <xref:System.Collections.Concurrent.BlockingCollection%601>, można określić nie tylko ograniczonej pojemności, ale również typem kolekcji do użycia.</span><span class="sxs-lookup"><span data-stu-id="b1e73-139">When you create a <xref:System.Collections.Concurrent.BlockingCollection%601>, you can specify not only the bounded capacity but also the type of collection to use.</span></span> <span data-ttu-id="b1e73-140">Na przykład można określić <xref:System.Collections.Concurrent.ConcurrentQueue%601> dla pierwszego w pierwszy limit zachowanie (FIFO) lub <xref:System.Collections.Concurrent.ConcurrentStack%601> ostatniego pierwszy LIFO zachowania.</span><span class="sxs-lookup"><span data-stu-id="b1e73-140">For example, you could specify a <xref:System.Collections.Concurrent.ConcurrentQueue%601> for first in-first out (FIFO) behavior, or a <xref:System.Collections.Concurrent.ConcurrentStack%601> for last in-first out (LIFO) behavior.</span></span> <span data-ttu-id="b1e73-141">Można użyć dowolnej klasy kolekcji, który implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b1e73-141">You can use any collection class that implements the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interface.</span></span> <span data-ttu-id="b1e73-142">Domyślny typ kolekcji dla <xref:System.Collections.Concurrent.BlockingCollection%601> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e73-142">The default collection type for <xref:System.Collections.Concurrent.BlockingCollection%601> is <xref:System.Collections.Concurrent.ConcurrentQueue%601>.</span></span> <span data-ttu-id="b1e73-143">W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Collections.Concurrent.BlockingCollection%601> ciągów, które ma pojemność 1000 i używa <xref:System.Collections.Concurrent.ConcurrentBag%601>:</span><span class="sxs-lookup"><span data-stu-id="b1e73-143">The following code example shows how to create a <xref:System.Collections.Concurrent.BlockingCollection%601> of strings that has a capacity of 1000 and uses a <xref:System.Collections.Concurrent.ConcurrentBag%601>:</span></span>  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 <span data-ttu-id="b1e73-144">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie ograniczenia i funkcji blokowania w kolekcji](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-144">For more information, see [How to: Add Bounding and Blocking Functionality to a Collection](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).</span></span>  
  
## <a name="ienumerable-support"></a><span data-ttu-id="b1e73-145">Obsługa interfejsu IEnumerable</span><span class="sxs-lookup"><span data-stu-id="b1e73-145">IEnumerable Support</span></span>  
 <span data-ttu-id="b1e73-146"><xref:System.Collections.Concurrent.BlockingCollection%601>udostępnia <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodę, która umożliwia klientom korzystać `foreach` (`For Each` w [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) na usuwanie elementów do czasu ukończenia kolekcji, co oznacza, że jest pusty i ma więcej elementów zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="b1e73-146"><xref:System.Collections.Concurrent.BlockingCollection%601> provides a <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method that enables consumers to use `foreach` (`For Each` in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) to remove items until the collection is completed, which means it is empty and no more items will be added.</span></span> <span data-ttu-id="b1e73-147">Aby uzyskać więcej informacji, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-147">For more information, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>  
  
## <a name="using-many-blockingcollections-as-one"></a><span data-ttu-id="b1e73-148">Przy użyciu wielu BlockingCollections wśród</span><span class="sxs-lookup"><span data-stu-id="b1e73-148">Using Many BlockingCollections As One</span></span>  
 <span data-ttu-id="b1e73-149">W scenariuszach, w których klient musi jednocześnie pobieranie elementów z wielu kolekcji, można utworzyć tablic <xref:System.Collections.Concurrent.BlockingCollection%601> i użyj metody statyczne, takiego jak <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> którego dodawanie do lub wykonać z dowolnego z kolekcji w programie Tablica.</span><span class="sxs-lookup"><span data-stu-id="b1e73-149">For scenarios in which a consumer needs to take items from multiple collections simultaneously, you can create arrays of <xref:System.Collections.Concurrent.BlockingCollection%601> and use the static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> that will add to or take from any of the collections in the array.</span></span> <span data-ttu-id="b1e73-150">Jeśli blokuje jednej kolekcji, metoda natychmiast próbuje innego dopóki nie zostanie znaleziony taki, który można wykonać operacji.</span><span class="sxs-lookup"><span data-stu-id="b1e73-150">If one collection is blocking, the method immediately tries another until it finds one that can perform the operation.</span></span> <span data-ttu-id="b1e73-151">Aby uzyskać więcej informacji, zobacz [porady: Użycie tablic blokowanie kolekcji w potoku](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).</span><span class="sxs-lookup"><span data-stu-id="b1e73-151">For more information, see [How to: Use Arrays of Blocking Collections in a Pipeline](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e73-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1e73-152">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="b1e73-153">Kolekcje i struktury danych</span><span class="sxs-lookup"><span data-stu-id="b1e73-153">Collections and Data Structures</span></span>](../../../../docs/standard/collections/index.md)  
 [<span data-ttu-id="b1e73-154">Kolekcje obsługujące wielowątkowość</span><span class="sxs-lookup"><span data-stu-id="b1e73-154">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)