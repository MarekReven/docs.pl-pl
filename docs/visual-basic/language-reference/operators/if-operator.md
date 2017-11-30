---
title: "If — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c553da5abf5453ba881671806b976125355c1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="40d22-102">If — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d22-102">If Operator (Visual Basic)</span></span>
<span data-ttu-id="40d22-103">Używa zwarcia oceny warunkowo zwracać jedną z dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="40d22-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="40d22-104">`If` Operator może zostać wywołany z trzech argumentów lub dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="40d22-104">The `If` operator can be called with three arguments or with two arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d22-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="40d22-105">Syntax</span></span>  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="40d22-106">Jeśli Operator wywołany z trzech argumentów</span><span class="sxs-lookup"><span data-stu-id="40d22-106">If Operator Called with Three Arguments</span></span>  
 <span data-ttu-id="40d22-107">Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi mieć wartość, która może być rzutowana jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="40d22-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="40d22-108">Czy `Boolean` wartość określa, które z dwóch argumentów jest obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="40d22-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="40d22-109">Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływana przy użyciu trzech argumentów.</span><span class="sxs-lookup"><span data-stu-id="40d22-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="40d22-110">Części</span><span class="sxs-lookup"><span data-stu-id="40d22-110">Parts</span></span>  
  
|<span data-ttu-id="40d22-111">Termin</span><span class="sxs-lookup"><span data-stu-id="40d22-111">Term</span></span>|<span data-ttu-id="40d22-112">Definicja</span><span class="sxs-lookup"><span data-stu-id="40d22-112">Definition</span></span>|  
|---|---|  
|`argument1`|<span data-ttu-id="40d22-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="40d22-113">Required.</span></span> <span data-ttu-id="40d22-114">`Boolean`.</span><span class="sxs-lookup"><span data-stu-id="40d22-114">`Boolean`.</span></span> <span data-ttu-id="40d22-115">Określa, który argumentów do oceny i zwracany.</span><span class="sxs-lookup"><span data-stu-id="40d22-115">Determines which of the other arguments to evaluate and return.</span></span>|  
|`argument2`|<span data-ttu-id="40d22-116">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="40d22-116">Required.</span></span> <span data-ttu-id="40d22-117">`Object`.</span><span class="sxs-lookup"><span data-stu-id="40d22-117">`Object`.</span></span> <span data-ttu-id="40d22-118">Jeśli obliczane i zwrócone `argument1` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="40d22-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|  
|`argument3`|<span data-ttu-id="40d22-119">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="40d22-119">Required.</span></span> <span data-ttu-id="40d22-120">`Object`.</span><span class="sxs-lookup"><span data-stu-id="40d22-120">`Object`.</span></span> <span data-ttu-id="40d22-121">Jeśli obliczane i zwrócone `argument1` daje w wyniku `False` lub, jeśli `argument1` jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="40d22-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|  
  
 <span data-ttu-id="40d22-122">`If` Operator, który jest wywoływany z trzech argumentów działa jak `IIf` funkcja ocena zwarcia z wyjątkiem tego, aby były używane.</span><span class="sxs-lookup"><span data-stu-id="40d22-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="40d22-123">`IIf` Funkcja zawsze ocenia wszystkich trzech argumentów, podczas gdy `If` operator, który używa trzech argumentów ocenia tylko dwa z nich.</span><span class="sxs-lookup"><span data-stu-id="40d22-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="40d22-124">Pierwszy `If` argument jest obliczane i wynikiem jest rzutowany jako `Boolean` wartość `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="40d22-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="40d22-125">Jeśli wartość jest `True`, `argument2` jest obliczany i zwracany jest jego wartość, ale `argument3` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="40d22-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="40d22-126">Jeśli wartość `Boolean` wyrażenie jest `False`, `argument3` jest obliczany i zwracany jest jego wartość, ale `argument2` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="40d22-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="40d22-127">Poniższe przykłady przedstawiają użycie `If` stosowania trzech argumentów:</span><span class="sxs-lookup"><span data-stu-id="40d22-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 <span data-ttu-id="40d22-128">Poniższy przykład przedstawia wartość ocena zwarcia.</span><span class="sxs-lookup"><span data-stu-id="40d22-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="40d22-129">W przykładzie przedstawiono dwie próby dzielenia zmiennej `number` przez zmienną `divisor` z wyjątkiem sytuacji, gdy `divisor` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="40d22-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="40d22-130">W takim przypadku powinna zostać zwrócona wartość 0, a nie powinny być podejmowane próby można wykonać podziału, ponieważ spowodowałoby to błąd czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40d22-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="40d22-131">Ponieważ `If` ocena zwarcia używa wyrażenia, oceniając drugiego i trzeciego argumentu, w zależności od wartości pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="40d22-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="40d22-132">Jeśli pierwszy argument ma wartość true, dzielnik nie jest zero i bezpiecznie oceń drugi argument i wykonać podziału.</span><span class="sxs-lookup"><span data-stu-id="40d22-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="40d22-133">Jeśli pierwszy argument ma wartość false, trzeci argument jest obliczane i jest zwracana wartość 0.</span><span class="sxs-lookup"><span data-stu-id="40d22-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="40d22-134">W związku z tym gdy dzielnik jest 0, nie są podejmowane próby do podziału i nie zwróciło żadnych wyników błędu.</span><span class="sxs-lookup"><span data-stu-id="40d22-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="40d22-135">Jednak ponieważ `IIf` nie używa ocena zwarcia, drugi argument jest obliczane, nawet wtedy, gdy pierwszy argument ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="40d22-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="40d22-136">Powoduje to błąd dzielenia przez zero w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40d22-136">This causes a run-time divide-by-zero error.</span></span>  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="40d22-137">Jeśli Operator wywołany z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="40d22-137">If Operator Called with Two Arguments</span></span>  
 <span data-ttu-id="40d22-138">Pierwszy argument `If` można pominąć.</span><span class="sxs-lookup"><span data-stu-id="40d22-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="40d22-139">Dzięki temu operatora, który można wywołać za pomocą tylko dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="40d22-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="40d22-140">Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływana z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="40d22-140">The following list applies only when the `If` operator is called with two arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="40d22-141">Części</span><span class="sxs-lookup"><span data-stu-id="40d22-141">Parts</span></span>  
  
|<span data-ttu-id="40d22-142">Termin</span><span class="sxs-lookup"><span data-stu-id="40d22-142">Term</span></span>|<span data-ttu-id="40d22-143">Definicja</span><span class="sxs-lookup"><span data-stu-id="40d22-143">Definition</span></span>|  
|---|---|  
|`argument2`|<span data-ttu-id="40d22-144">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="40d22-144">Required.</span></span> <span data-ttu-id="40d22-145">`Object`.</span><span class="sxs-lookup"><span data-stu-id="40d22-145">`Object`.</span></span> <span data-ttu-id="40d22-146">Musi być odwołanie lub typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="40d22-146">Must be a reference or nullable type.</span></span> <span data-ttu-id="40d22-147">Obliczany i zwracany, jeśli wynikiem jego obliczenia cokolwiek innego niż `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="40d22-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|  
|`argument3`|<span data-ttu-id="40d22-148">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="40d22-148">Required.</span></span> <span data-ttu-id="40d22-149">`Object`.</span><span class="sxs-lookup"><span data-stu-id="40d22-149">`Object`.</span></span> <span data-ttu-id="40d22-150">Jeśli obliczane i zwrócone `argument2` daje w wyniku `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="40d22-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|  
  
 <span data-ttu-id="40d22-151">Gdy `Boolean` argument zostanie pominięty, pierwszy argument musi być odwołanie lub typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="40d22-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable type.</span></span> <span data-ttu-id="40d22-152">Jeśli pierwszy argument ma wartość `Nothing`, jest zwracana wartość drugiego argumentu.</span><span class="sxs-lookup"><span data-stu-id="40d22-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="40d22-153">We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="40d22-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="40d22-154">Poniższy przykład przedstawia sposób działania tej oceny.</span><span class="sxs-lookup"><span data-stu-id="40d22-154">The following example illustrates how this evaluation works.</span></span>  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="40d22-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40d22-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [<span data-ttu-id="40d22-156">Typy dopuszczające wartości zerowe wartości</span><span class="sxs-lookup"><span data-stu-id="40d22-156">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="40d22-157">Nothing</span><span class="sxs-lookup"><span data-stu-id="40d22-157">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)