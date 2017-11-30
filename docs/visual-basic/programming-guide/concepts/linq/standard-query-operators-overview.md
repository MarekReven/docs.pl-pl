---
title: "Operatory standardowe zapytań — omówienie (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f9ad39b4890455f7d03f0b9bbfc51264d98d56b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="c9213-102">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="c9213-103">*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="c9213-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="c9213-104">Większość tych metod działają w sekwencji, w którym sekwencja jest obiekt, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c9213-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="c9213-105">Standardowe operatory zapytań zapewniają możliwość wykonywania kwerend włącznie z filtrowaniem projekcji, agregacji, sortowania i inne.</span><span class="sxs-lookup"><span data-stu-id="c9213-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="c9213-106">Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i inne, który działa na obiektach typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="c9213-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c9213-107">Statyczne elementy członkowskie są metody, wchodzące w skład każdego zestawu <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c9213-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="c9213-108">Są one zdefiniowane jako *metody rozszerzenia* typu, które działają na.</span><span class="sxs-lookup"><span data-stu-id="c9213-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="c9213-109">Oznacza to, że może być wywoływana za pomocą składni metody statycznej lub składnia metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c9213-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="c9213-110">Ponadto kilka metod operator zapytania standardowe działania dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="c9213-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c9213-111"><xref:System.Linq.Enumerable> Typ definiuje dwie metody takie że działają zarówno na obiektach typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="c9213-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="c9213-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć bez parametrów lub inny niż ogólny kolekcji w wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="c9213-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="c9213-113">Do tworzenia kolekcji silnie typizowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c9213-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="c9213-114"><xref:System.Linq.Queryable> Klasy definiuje dwie metody podobne, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="c9213-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="c9213-115">Standardowe operatory zapytań różnią się czas ich działania, w zależności od tego, czy zwracać wartość pojedynczą lub sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="c9213-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="c9213-116">Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) wykonaj natychmiast.</span><span class="sxs-lookup"><span data-stu-id="c9213-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="c9213-117">Metody zwracające sekwencję wstrzymuje wykonywanie zapytania i zwracać obiekt wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="c9213-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="c9213-118">W przypadku metod, które pracują na kolekcje w pamięci, czyli tych metod, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwrócony obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="c9213-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="c9213-119">Po wyliczeniu tego obiektu jest zastosować logiki — operator zapytań i są zwracane wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9213-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="c9213-120">Z kolei metody który rozszerzyć <xref:System.Linq.IQueryable%601> nie implementuje wszystkie zachowania podczas badania, ale kompilacji drzewo wyrażenia, które reprezentuje zapytanie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="c9213-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="c9213-121">Przetwarzanie zapytania jest obsługiwane przez źródło <xref:System.Linq.IQueryable%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9213-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="c9213-122">Wywołania metod zapytania można połączyć ze sobą w jednym zapytaniu, dzięki czemu staną się arbitralnie złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="c9213-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="c9213-123">W poniższym przykładzie kodu pokazano, jak standardowe operatory kwerend może służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c9213-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="c9213-124">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="c9213-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="c9213-125">Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane C# i Visual Basic składni słowa kluczowego języka, umożliwiający ich można wywołać w ramach *zapytania* *wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="c9213-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="c9213-126">Aby uzyskać więcej informacji o standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni, zobacz [składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c9213-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="c9213-127">Rozszerzenie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="c9213-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="c9213-128">Zbiór standardowych operatorów zapytań można rozszerzyć, aby tworzenie metod specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="c9213-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="c9213-129">Standardowe operatory zapytań można także zastąpić własne implementacje, które udostępniają dodatkowe usługi, takie jak zdalne oceny, translacja zapytania i optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="c9213-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="c9213-130">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.</span><span class="sxs-lookup"><span data-stu-id="c9213-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c9213-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c9213-131">Related Sections</span></span>  
 <span data-ttu-id="c9213-132">Poniższe łącza prowadzą do tematów zawierających dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcje.</span><span class="sxs-lookup"><span data-stu-id="c9213-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="c9213-133">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="c9213-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="c9213-134">Operacje na zestawie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="c9213-135">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="c9213-136">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="c9213-137">Operacje rzutowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="c9213-138">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="c9213-139">Dołącz do operacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="c9213-140">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="c9213-141">Operacje generowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="c9213-142">Operacje równości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="c9213-143">Operacje na elementach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="c9213-144">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="c9213-145">Operacje łączenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="c9213-146">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9213-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9213-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="c9213-148">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c9213-149">Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="c9213-150">Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9213-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="c9213-151">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="c9213-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)