---
title: "Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)"
ms.date: 05/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: "44"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: af7de7ea0be5368371e4bb174f6313e98f93ac4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="11dd3-102">Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="11dd3-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="11dd3-103">Typy dopuszczające wartości null są wystąpieniami klasy <xref:System.Nullable%601?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="11dd3-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="11dd3-104">Typ dopuszczający wartość null może reprezentować poprawny zakres wartości dla jego typem podstawowym wartości, a także dodatkowe `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="11dd3-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="11dd3-105">Na przykład `Nullable<Int32>`, wyraźnym "Dopuszcza wartości null z Int32," można przypisać wartości od -2147483648 do 2147483647 lub można go przypisać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="11dd3-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="11dd3-106">A `Nullable<bool>` można przypisać wartości [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), lub [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="11dd3-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="11dd3-107">Możliwość przypisania `null` do typów liczbowych i logicznych jest szczególnie przydatne podczas mamy do czynienia z bazami danych i inne typy danych, które zawierają elementy, które nie może być przypisana wartość.</span><span class="sxs-lookup"><span data-stu-id="11dd3-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="11dd3-108">Na przykład polem w bazie danych można zapisać wartości `true` lub `false`, lub może być niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="11dd3-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="11dd3-109">Aby uzyskać więcej przykładów, zobacz [przy użyciu typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span><span class="sxs-lookup"><span data-stu-id="11dd3-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="11dd3-110">Typy dopuszczające wartości zerowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="11dd3-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="11dd3-111">Typy dopuszczające wartości zerowe mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="11dd3-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="11dd3-112">Typy dopuszczające wartości zerowe reprezentuje typ wartości zmiennych, które można przypisać wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="11dd3-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="11dd3-113">Nie można utworzyć typu zerowalnego na podstawie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="11dd3-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="11dd3-114">(Odniesienia obsługują typy już `null` wartości.)</span><span class="sxs-lookup"><span data-stu-id="11dd3-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="11dd3-115">Składnia `T?` jest skróconą formą <xref:System.Nullable%601>, gdzie `T` jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="11dd3-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="11dd3-116">Dwa formularze są wymienne.</span><span class="sxs-lookup"><span data-stu-id="11dd3-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="11dd3-117">Przypisywanie wartości do typu dopuszczającego wartość null, tak samo jak dla typu wartości zwykłej, na przykład `int? x = 10;` lub `double? d = 4.108`.</span><span class="sxs-lookup"><span data-stu-id="11dd3-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="11dd3-118">Typ dopuszczający wartość NULL można również przypisać wartość `null`:`int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="11dd3-118">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="11dd3-119">Użyj <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metodę, aby zwrócić przypisaną wartość lub wartość domyślna dla typu źródłowego, jeśli wartość jest `null`, na przykład`int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="11dd3-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="11dd3-120">Użyj <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości tylko do odczytu do testowania w przypadku wartości null i pobrać wartość, jak pokazano w poniższym przykładzie:`if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="11dd3-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="11dd3-121">`HasValue` Zwraca `true` Jeśli zmienna zawiera wartość, lub `false` przypadku `null`.</span><span class="sxs-lookup"><span data-stu-id="11dd3-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="11dd3-122">`Value` Właściwość zwraca wartość, jeśli jeden jest przypisany.</span><span class="sxs-lookup"><span data-stu-id="11dd3-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="11dd3-123">W przeciwnym razie <xref:System.InvalidOperationException?displayProperty=nameWithType> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="11dd3-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="11dd3-124">Wartość domyślna dla `HasValue` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="11dd3-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="11dd3-125">`Value` Właściwość nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="11dd3-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="11dd3-126">Można również użyć `==` i `!=` operatory typu dopuszczającego wartość null, jak pokazano w poniższym przykładzie:`if (x != null) y = x;`</span><span class="sxs-lookup"><span data-stu-id="11dd3-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="11dd3-127">Użyj `??` operatora, aby przypisać wartość domyślną, który zostanie zastosowany, gdy typ dopuszczający wartość null, w których bieżąca wartość jest `null` jest przypisany do typu wartości null, na przykład`int? x = null; int y = x ?? -1;`</span><span class="sxs-lookup"><span data-stu-id="11dd3-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="11dd3-128">Zagnieżdżone typy dopuszczające wartości null są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="11dd3-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="11dd3-129">Następujący wiersz nie zostanie skompilowany:`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="11dd3-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11dd3-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="11dd3-130">Related Sections</span></span>  
 <span data-ttu-id="11dd3-131">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="11dd3-131">For more information:</span></span>  
  
-   [<span data-ttu-id="11dd3-132">Przy użyciu typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="11dd3-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="11dd3-133">Konwersja boxing typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="11dd3-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="11dd3-134">?? Operator</span><span class="sxs-lookup"><span data-stu-id="11dd3-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="11dd3-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11dd3-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11dd3-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11dd3-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="11dd3-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11dd3-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11dd3-138">C#</span><span class="sxs-lookup"><span data-stu-id="11dd3-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="11dd3-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="11dd3-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="11dd3-140">Co dokładnie "unosiło" oznacza?</span><span class="sxs-lookup"><span data-stu-id="11dd3-140">What exactly does 'lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112382)