---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="a8d6f-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8d6f-102">Key (Visual Basic)</span></span>
<span data-ttu-id="a8d6f-103">`Key` — Słowo kluczowe można określić zachowanie dla właściwości typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="a8d6f-104">Tylko właściwości wyznaczone jako właściwości klucza brać udziału w testach równość wystąpień typu anonimowego lub obliczenia wartości skrótu kodu.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="a8d6f-105">Nie można zmienić wartości właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="a8d6f-106">Możesz określić właściwości typu anonimowego jako właściwość klucza przez umieszczenie słowo kluczowe `Key` przed jej deklaracją listy inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="a8d6f-107">W poniższym przykładzie `Airline` i `FlightNo` są właściwościami klucza, ale `Gate` nie jest.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="a8d6f-108">Podczas tworzenia nowego typu anonimowego dziedziczy bezpośrednio z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="a8d6f-109">Kompilator zastępuje trzy dziedziczone elementy członkowskie: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="a8d6f-110">Kod zastąpienia, który jest tworzony dla <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> na podstawie właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="a8d6f-111">Jeśli nie ma żadnych właściwości klucza w typie, <xref:System.Object.GetHashCode%2A> i <xref:System.Object.Equals%2A> nie zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="a8d6f-112">Równość</span><span class="sxs-lookup"><span data-stu-id="a8d6f-112">Equality</span></span>  
 <span data-ttu-id="a8d6f-113">Dwa wystąpienia typu anonimowego są takie same, jeśli są one wystąpień tego samego typu i wartości ich właściwości klucza są takie same.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="a8d6f-114">W poniższych przykładach `flight2` jest równa `flight1` z poprzedniego przykładu ponieważ są one takie same anonimowego wystąpienia typu i mieć zgodne wartości dla ich właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="a8d6f-115">Jednak `flight3` nie jest równa `flight1` , ponieważ ma ona inną wartość dla właściwości klucza, `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="a8d6f-116">Wystąpienie `flight4` nie jest taki sam typ jak `flight1` ponieważ one określić różne właściwości jako właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="a8d6f-117">Jeśli dwa wystąpienia został zadeklarowany z tylko niż właściwości klucza, takie same jak w nazwę, typ, kolejność i wartości, dwa wystąpienia nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="a8d6f-118">Wystąpienia bez właściwości klucza wynosi tylko do samego siebie.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="a8d6f-119">Aby uzyskać więcej informacji o warunkach, w których dwa wystąpienia typu anonimowego są wystąpień tego samego typu anonimowego, zobacz [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8d6f-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="a8d6f-120">Obliczanie kodu wyznaczania wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="a8d6f-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="a8d6f-121">Podobnie jak <xref:System.Object.Equals%2A>, funkcji skrótu, który jest zdefiniowany w <xref:System.Object.GetHashCode%2A> dla typu anonimowego opiera się na typ właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="a8d6f-122">W poniższych przykładach pokazano interakcji między właściwości klucza oraz skrót wartości kodów.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="a8d6f-123">Wystąpienia typu anonimowego, które mają takie same wartości dla wszystkich właściwości klucza mają taką samą wartość kodu wyznaczania wartości skrótu, nawet jeśli niż właściwości klucza nie ma dopasowania wartości.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="a8d6f-124">Zwraca następująca instrukcja `True`.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="a8d6f-125">Wystąpienia typu anonimowego, które mają różne wartości dla co najmniej jednej właściwości klucza mają różne skrótu kodu wartości.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="a8d6f-126">Zwraca następująca instrukcja `False`.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="a8d6f-127">Wystąpień typów anonimowych, które określają różne właściwości jako właściwości klucza nie są wystąpień tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="a8d6f-128">Mają one wartości kodów różnych wyznaczania wartości skrótu, nawet wtedy, gdy nazwy i wartości wszystkich właściwości są takie same.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="a8d6f-129">Zwraca następująca instrukcja `False`.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="a8d6f-130">Wartości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a8d6f-130">Read-Only Values</span></span>  
 <span data-ttu-id="a8d6f-131">Nie można zmienić wartości właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="a8d6f-132">Na przykład w `flight1` w przykładach wcześniejszych `Airline` i `FlightNo` pola są tylko do odczytu, ale `Gate` można zmienić.</span><span class="sxs-lookup"><span data-stu-id="a8d6f-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a8d6f-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8d6f-133">See Also</span></span>  
 [<span data-ttu-id="a8d6f-134">Definicja typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="a8d6f-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="a8d6f-135">Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="a8d6f-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="a8d6f-136">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="a8d6f-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)