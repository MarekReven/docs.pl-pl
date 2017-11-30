---
title: invalidCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c051e1513f8e8ad1735085cb93f106b4fb9b0d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidcercall-mda"></a><span data-ttu-id="6036e-102">invalidCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="6036e-102">invalidCERCall MDA</span></span>
<span data-ttu-id="6036e-103">`invalidCERCall` Zarządzany Asystent debugowania (MDA) została aktywowana po wywołaniu wykresu (CER) region ograniczonego wykonania metody, która ma nie kontraktu niezawodności lub zbyt słabe kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6036e-103">The `invalidCERCall` managed debugging assistant (MDA) is activated when there is a call within the constrained execution region (CER) graph to a method that has no reliability contract or an excessively weak contract.</span></span> <span data-ttu-id="6036e-104">Kontrakt słabe jest kontraktu, który deklaruje, że najgorszy uszkodzenie wielkość stanu jest zakresu większy niż wystąpienie przekazany do wywołania, oznacza to, <xref:System.AppDomain> lub stan procesu może ulec uszkodzeniu lub jego wynik nie jest zawsze sposób niejednoznaczny Obliczanie gdy jest wywoływany w CER.</span><span class="sxs-lookup"><span data-stu-id="6036e-104">A weak contract is a contract that declares that the worst case state corruption is of greater scope than the instance passed to the call, that is, the <xref:System.AppDomain> or process state may become corrupted or that its result is not always deterministically computable when called within a CER.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6036e-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="6036e-105">Symptoms</span></span>  
 <span data-ttu-id="6036e-106">Nieoczekiwane wyniki podczas wykonywania kodu w CER.</span><span class="sxs-lookup"><span data-stu-id="6036e-106">Unexpected results when executing code in a CER.</span></span> <span data-ttu-id="6036e-107">Objawy nie są określone.</span><span class="sxs-lookup"><span data-stu-id="6036e-107">The symptoms are not specific.</span></span> <span data-ttu-id="6036e-108">Może być nieoczekiwane <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, lub inne wyjątków w wywołaniu metody zawodnych ponieważ środowisko uruchomieniowe nie wcześniejsze przygotowanie ani go chronić <xref:System.Threading.ThreadAbortException> wyjątków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6036e-108">They could be an unexpected <xref:System.OutOfMemoryException>, a <xref:System.Threading.ThreadAbortException>, or other exceptions at the call into the unreliable method because the runtime did not prepare it ahead of time or protect it from <xref:System.Threading.ThreadAbortException> exceptions at run time.</span></span> <span data-ttu-id="6036e-109">Większe zagrożenie jest, że wszystkie wyjątki wynikające z metody w czasie wykonywania można pozostawić <xref:System.AppDomain> lub procesów w niestabilnym stanie, czyli sprzeczności z celem CER.</span><span class="sxs-lookup"><span data-stu-id="6036e-109">A greater threat is that any exception resulting from the method at run time could leave the <xref:System.AppDomain> or process in an unstable state, which is contrary to the objective of a CER.</span></span> <span data-ttu-id="6036e-110">Utworzone CER dzieje się tak aby uniknąć uszkodzenia stanu, takich jak ta.</span><span class="sxs-lookup"><span data-stu-id="6036e-110">The reason a CER is created is to avoid state corruptions such as this.</span></span> <span data-ttu-id="6036e-111">Objawy uszkodzonego są określone dla aplikacji definicji spójna różni się między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="6036e-111">The symptoms of corrupt state are application specific because the definition of consistent state is different between applications.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6036e-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6036e-112">Cause</span></span>  
 <span data-ttu-id="6036e-113">Kod w CER powoduje wywołanie funkcji bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> lub niska <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> który nie jest zgodny z systemem w CER.</span><span class="sxs-lookup"><span data-stu-id="6036e-113">Code within a CER is calling a function with no <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> or with a weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> that is not compatible with running in a CER.</span></span>  
  
 <span data-ttu-id="6036e-114">W odniesieniu do składni kontraktu niezawodności, kontrakt słabe jest kontraktu, która nie określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość wyliczenia lub Określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, lub <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span><span class="sxs-lookup"><span data-stu-id="6036e-114">In terms of reliability contract syntax, a weak contract is a contract that does not specify a <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration value or specifies a <xref:System.Runtime.ConstrainedExecution.Consistency> value of <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, or <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="6036e-115">Jeden z następujących warunków wskazuje, że kod wywołuje może utrudnić próby Obsługa spójna innego kodu w CER.</span><span class="sxs-lookup"><span data-stu-id="6036e-115">Any of these conditions indicates that the code called may impede the efforts of the other code in the CER to maintain consistent state.</span></span>  <span data-ttu-id="6036e-116">CERs umożliwić kodu traktować błędy w sposób bardzo deterministyczna, obsługa invariants wewnętrznego, które są ważne dla aplikacji, dzięki czemu jego dalsze działanie jest w fazie przejściowej błędów, takich jak wyjątki o braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="6036e-116">CERs allow code to treat errors in a very deterministic manner, maintaining internal invariants that are important to the application and allowing it to continue running in the face of transient errors such as out-of-memory exceptions.</span></span>  
  
 <span data-ttu-id="6036e-117">Aktywacja to zdarzenie MDA wskazuje możliwość metoda wywoływana w CER może zakończyć się niepowodzeniem w sposób zapewniający element wywołujący nie oczekiwano lub który pozostawia <xref:System.AppDomain> lub przetworzyć stan uszkodzony lub ich nieodwracalnej utraty.</span><span class="sxs-lookup"><span data-stu-id="6036e-117">The activation of this MDA indicates a possibility the method being called in the CER can fail in a way that the caller did not expect or that leaves the <xref:System.AppDomain> or process state corrupted or unrecoverable.</span></span> <span data-ttu-id="6036e-118">Oczywiście wywoływanego kodu może zostać prawidłowo wykonany, a problem jest po prostu nieistniejącego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6036e-118">Of course, the called code might execute correctly and the problem is simply a missing contract.</span></span> <span data-ttu-id="6036e-119">Jednak zagadnień związanych z pisanie niezawodnego kodu są niewielkie i brak kontrakt jest dobry wskaźnik, którego kod może nie zostać prawidłowo wykonany.</span><span class="sxs-lookup"><span data-stu-id="6036e-119">However, the issues involved in writing reliable code are subtle and the absence of a contract is a good indicator the code might not execute correctly.</span></span> <span data-ttu-id="6036e-120">Kontrakty te z nich są wskaźnikami programistę zawiera kodowany niezawodnie, a także gwarantuje, że te gwarancje nie zmieni się w przyszłości poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="6036e-120">The contracts are indicators that the programmer has coded reliably and also promises that these guarantees will not change in future revisions of the code.</span></span>  <span data-ttu-id="6036e-121">Oznacza to, że kontrakty te są deklaracje zamierzone i nie tylko szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="6036e-121">That is, the contracts are declarations of intent and not just implementation details.</span></span>  
  
 <span data-ttu-id="6036e-122">Ponieważ dowolnej metody z kontraktem słabych lub nieistniejącą mogą ulec awarii w wielu nieprzewidywalnych sposobów, środowisko uruchomieniowe nie jest podejmowana próba Usuń wszystkie własną nieprzewidywalne błędów z metody, które zostały wprowadzone przez opóźnieniem JIT — kompilowanie, słownika ogólne wypełnianie lub wątku jest przerywana, np.</span><span class="sxs-lookup"><span data-stu-id="6036e-122">Because any method with a weak or nonexistent contract can potentially fail in many unpredictable ways, the runtime does not attempt to remove any of its own unpredictable failures from the method  that are introduced by lazy JIT-compiling, generics dictionary population, or thread aborts, for example.</span></span> <span data-ttu-id="6036e-123">Oznacza to po aktywowaniu to zdarzenie MDA wskazuje on, że środowisko wykonawcze nie zawiera wywołaną metodę w CER definiowanego; wykresu wywołań zostało zakończone w tym węźle, ponieważ kontynuowanie przygotowanie to poddrzewo byłaby pomocna zamaskować potencjalnych błędów.</span><span class="sxs-lookup"><span data-stu-id="6036e-123">That is, when this MDA is activated, it indicates that the runtime did not include the called method in the CER being defined; the call graph was terminated at this node because continuing to prepare this subtree would help mask the potential error.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6036e-124">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6036e-124">Resolution</span></span>  
 <span data-ttu-id="6036e-125">Dodaj kontrakt niezawodności prawidłowy funkcji lub Unikaj używania tego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="6036e-125">Add a valid reliability contract to the function or avoid using that function call.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6036e-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6036e-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="6036e-127">Efekt wywoływanie słabe umowy z CER może być błąd CER do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="6036e-127">The effect of calling a weak contract from a CER could be the CER failure to complete its operations.</span></span> <span data-ttu-id="6036e-128">Może to spowodować uszkodzenie <xref:System.AppDomain> przetworzyć stanu.</span><span class="sxs-lookup"><span data-stu-id="6036e-128">This could lead to corruption of the <xref:System.AppDomain> process state.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6036e-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6036e-129">Output</span></span>  
 <span data-ttu-id="6036e-130">Poniżej przedstawiono przykładowe dane wyjściowe to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="6036e-130">The following is sample output from this MDA.</span></span>  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a><span data-ttu-id="6036e-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6036e-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6036e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6036e-132">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="6036e-133">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="6036e-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)