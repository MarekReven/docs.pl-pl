---
title: 'Porady: implementowanie obserwatora'
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
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="42e73-102">Porady: implementowanie obserwatora</span><span class="sxs-lookup"><span data-stu-id="42e73-102">How to: Implement an Observer</span></span>
<span data-ttu-id="42e73-103">Wzorzec projektowy obserwatora wymaga podziału między obserwatora, który służy do rejestrowania dla powiadomień, a dostawcę, który monitoruje danych i wysyła powiadomienia do co najmniej jeden obserwatorów.</span><span class="sxs-lookup"><span data-stu-id="42e73-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="42e73-104">W tym temacie omówiono sposób tworzenia obserwatora.</span><span class="sxs-lookup"><span data-stu-id="42e73-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="42e73-105">Pokrewnego tematu, [porady: implementowania dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md), w tym artykule omówiono sposób tworzenia dostawcy.</span><span class="sxs-lookup"><span data-stu-id="42e73-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="42e73-106">Aby utworzyć obserwatora</span><span class="sxs-lookup"><span data-stu-id="42e73-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="42e73-107">Zdefiniuj obserwatora, który jest typem, który implementuje <xref:System.IObserver%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42e73-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="42e73-108">Na przykład poniższy kod definiuje typu o nazwie `TemperatureReporter` czyli skonstruowane <xref:System.IObserver%601?displayProperty=nameWithType> implementacji z argumentem typu ogólnego `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="42e73-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="42e73-109">Jeśli obserwatora zrezygnować z otrzymywania powiadomień przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji, zdefiniuj zmiennej prywatnej, w którym będą przechowywane <xref:System.IDisposable> implementacji zwrócona przez dostawcę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> — metoda.</span><span class="sxs-lookup"><span data-stu-id="42e73-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42e73-110">Należy również definiować metody subskrypcji, która wywołuje metody dostawcy <xref:System.IObservable%601.Subscribe%2A> — metoda i magazyny zwróconego <xref:System.IDisposable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e73-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="42e73-111">Na przykład poniższy kod definiuje prywatnej zmiennej o nazwie `unsubscriber` i definiuje `Subscribe` metodę, która wywołuje metody dostawcy <xref:System.IObservable%601.Subscribe%2A> — metoda i przypisuje zwrócony obiekt do `unsubscriber` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42e73-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="42e73-112">Zdefiniuj metodę, która umożliwia obserwatora przestać otrzymywać powiadomienia przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> wykonania, jeśli ta funkcja jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="42e73-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="42e73-113">W poniższym przykładzie zdefiniowano `Unsubscribe` metody.</span><span class="sxs-lookup"><span data-stu-id="42e73-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="42e73-114">Podaj implementacje trzy metody zdefiniowane przez <xref:System.IObserver%601> interfejsu: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42e73-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="42e73-115">W zależności od potrzeb aplikacji i dostawcy <xref:System.IObserver%601.OnError%2A> i <xref:System.IObserver%601.OnCompleted%2A> metody mogą być stub implementacji.</span><span class="sxs-lookup"><span data-stu-id="42e73-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="42e73-116">Należy pamiętać, że <xref:System.IObserver%601.OnError%2A> — metoda nie powinna obsługiwać przekazany <xref:System.Exception> obiektu jako wyjątek i <xref:System.IObserver%601.OnCompleted%2A> metoda jest bezpłatna do wywoływania dostawcy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="42e73-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="42e73-117">W poniższym przykładzie przedstawiono <xref:System.IObserver%601> implementacja `TemperatureReporter` klasy.</span><span class="sxs-lookup"><span data-stu-id="42e73-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="42e73-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="42e73-118">Example</span></span>  
 <span data-ttu-id="42e73-119">Poniżej przedstawiono przykład zawierający kod źródłowy pełną `TemperatureReporter` klasy, która dostarcza <xref:System.IObserver%601> implementacji dla temperatury monitorowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42e73-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="42e73-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42e73-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="42e73-121">Wzorzec projektowy obserwatora</span><span class="sxs-lookup"><span data-stu-id="42e73-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="42e73-122">Porady: Implementowanie dostawcy</span><span class="sxs-lookup"><span data-stu-id="42e73-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="42e73-123">Wzorzec projektowy obserwatora — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="42e73-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)