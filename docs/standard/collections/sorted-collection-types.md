---
title: "Sortowane typów kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f23a69a8e2493e018b0a37628762247c0e33430
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorted-collection-types"></a><span data-ttu-id="4e599-102">Sortowane typów kolekcji</span><span class="sxs-lookup"><span data-stu-id="4e599-102">Sorted Collection Types</span></span>
<span data-ttu-id="4e599-103"><xref:System.Collections.SortedList?displayProperty=nameWithType> Klasy <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> klasy ogólnej i <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> klasy ogólnej są podobne do <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> ogólnej klasy w tym wdrażają <xref:System.Collections.IDictionary> interfejsu, ale obsługa ich kolejność elementów w sortowania według klucza, a nie mają O(1) wstawiania i pobierania charakterystycznych dla tablic skrótów.</span><span class="sxs-lookup"><span data-stu-id="4e599-103">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="4e599-104">Trzy klasy mają kilka funkcji cechy wspólne:</span><span class="sxs-lookup"><span data-stu-id="4e599-104">The three classes have several features in common:</span></span>  
  
-   <span data-ttu-id="4e599-105">Wszystkie trzy klasy implementować <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4e599-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="4e599-106">Dwie klasy rodzajowe także implementować <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="4e599-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>  
  
-   <span data-ttu-id="4e599-107">Każdy element jest parę klucza i wartości dla celów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4e599-107">Each element is a key/value pair for enumeration purposes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e599-108">Nongeneric <xref:System.Collections.SortedList> klasy zwraca <xref:System.Collections.DictionaryEntry> obiektów po wyliczone, mimo że zwracać dwa typy ogólne <xref:System.Collections.Generic.KeyValuePair%602> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e599-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>  
  
-   <span data-ttu-id="4e599-109">Elementy są sortowane według <xref:System.Collections.IComparer?displayProperty=nameWithType> implementacji (dla nongeneric <xref:System.Collections.SortedList>) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji (dwie klasy ogólnego).</span><span class="sxs-lookup"><span data-stu-id="4e599-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>  
  
-   <span data-ttu-id="4e599-110">Każda klasa udostępnia właściwości, które zwracają kolekcje zawierające tylko klucze lub tylko wartości.</span><span class="sxs-lookup"><span data-stu-id="4e599-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>  
  
 <span data-ttu-id="4e599-111">W poniższej tabeli przedstawiono niektóre różnice między dwoma klasami posortowaną listę i <xref:System.Collections.Generic.SortedDictionary%602> klasy.</span><span class="sxs-lookup"><span data-stu-id="4e599-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>  
  
|<span data-ttu-id="4e599-112"><xref:System.Collections.SortedList>Klasa nierodzajowe i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="4e599-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span>|<span data-ttu-id="4e599-113"><xref:System.Collections.Generic.SortedDictionary%602>Klasa ogólna</span><span class="sxs-lookup"><span data-stu-id="4e599-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="4e599-114">Właściwości, które zwracają kluczy i wartości są indeksowane, umożliwiając wydajne indeksowana pobierania.</span><span class="sxs-lookup"><span data-stu-id="4e599-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span>|<span data-ttu-id="4e599-115">Nie indeksowanego pobierania.</span><span class="sxs-lookup"><span data-stu-id="4e599-115">No indexed retrieval.</span></span>|  
|<span data-ttu-id="4e599-116">Pobieranie jest O (dziennika `n`).</span><span class="sxs-lookup"><span data-stu-id="4e599-116">Retrieval is O(log `n`).</span></span>|<span data-ttu-id="4e599-117">Pobieranie jest O (dziennika `n`).</span><span class="sxs-lookup"><span data-stu-id="4e599-117">Retrieval is O(log `n`).</span></span>|  
|<span data-ttu-id="4e599-118">Wstawianie i usuwanie są zwykle O (`n`), jednak wstawiania jest O (dziennika `n`) dla danych, które już znajdują się w kolejności sortowania, dzięki czemu każdy element zostanie dodany na końcu listy.</span><span class="sxs-lookup"><span data-stu-id="4e599-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="4e599-119">(Przy założeniu, że zmiany rozmiaru nie jest wymagane.)</span><span class="sxs-lookup"><span data-stu-id="4e599-119">(This assumes that a resize is not required.)</span></span>|<span data-ttu-id="4e599-120">Wstawianie i usuwanie są O (dziennika `n`).</span><span class="sxs-lookup"><span data-stu-id="4e599-120">Insertion and removal are O(log `n`).</span></span>|  
|<span data-ttu-id="4e599-121">Wykorzystuje mniej pamięci niż <xref:System.Collections.Generic.SortedDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="4e599-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span>|<span data-ttu-id="4e599-122">Używa więcej pamięci niż <xref:System.Collections.SortedList> nierodzajowe klasy i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="4e599-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span>|  
  
 <span data-ttu-id="4e599-123">Posortowane list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, która jest pochodną <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="4e599-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e599-124">Wartości, które zawierają własne klucze (na przykład pracownik rekordy, które zawierają numer identyfikacyjny), można utworzyć kolekcji kluczem, w której niektóre właściwości listy i niektóre właściwości słownika przez wynikających z <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólne Klasa.</span><span class="sxs-lookup"><span data-stu-id="4e599-124">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
 <span data-ttu-id="4e599-125">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> klasa udostępnia własnym równoważenia drzewa, która przechowuje dane posortowane po operacji wstawienia, usuwanie i wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="4e599-125">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="4e599-126">Ta klasa i <xref:System.Collections.Generic.HashSet%601> implementacji klasy <xref:System.Collections.Generic.ISet%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4e599-126">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e599-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e599-127">See Also</span></span>  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [<span data-ttu-id="4e599-128">Często używane typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="4e599-128">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)