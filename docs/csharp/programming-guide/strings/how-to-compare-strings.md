---
title: "Porady: porównywanie ciągów (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4837fa57c962cba841ffcc83c5bd4475a4faff0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-strings-c-programming-guide"></a><span data-ttu-id="ee54b-102">Porady: porównywanie ciągów (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="ee54b-102">How to: Compare strings (C# Programming Guide)</span></span>

<span data-ttu-id="ee54b-103">Podczas porównywania ciągów są generująca wynik informacją jednego ciągu jest większa lub mniejsza niż drugi lub czy dwa ciągi są takie same.</span><span class="sxs-lookup"><span data-stu-id="ee54b-103">When you compare strings, you are producing a result that says one string is greater than or less than the other, or that the two strings are equal.</span></span> <span data-ttu-id="ee54b-104">Zasady, według których ustalić wyniku są różne w zależności od tego, czy działają *porównanie liczby porządkowej* lub *porównania z uwzględnieniem kultury*.</span><span class="sxs-lookup"><span data-stu-id="ee54b-104">The rules by which the result is determined are different depending on whether you are performing *ordinal comparison* or *culture-sensitive comparison*.</span></span> <span data-ttu-id="ee54b-105">Należy użyć poprawny typ porównania dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="ee54b-105">It is important to use the correct kind of comparison for the specific task.</span></span>

 <span data-ttu-id="ee54b-106">Podstawowe liczby porządkowej porównania należy użyć w przypadku do porównywania lub posortować wartości dwa ciągi niezależnie konwencje językowe.</span><span class="sxs-lookup"><span data-stu-id="ee54b-106">Use basic ordinal comparisons when you have to compare or sort the values of two strings without regard to linguistic conventions.</span></span> <span data-ttu-id="ee54b-107">Porównanie liczby porządkowej podstawowe (`System.StringComparison.Ordinal`) jest rozróżniana wielkość liter, co oznacza, że dwa ciągi musi odpowiadać znaków dla znaku: "i" nie równa się "I" lub "I".</span><span class="sxs-lookup"><span data-stu-id="ee54b-107">A basic ordinal comparison (`System.StringComparison.Ordinal`) is case-sensitive, which means that the two strings must match character for character: "and" does not equal "And" or "AND".</span></span> <span data-ttu-id="ee54b-108">Jest odmianą często używane `System.StringComparison.OrdinalIgnoreCase`, która będzie odpowiadała "i", "I" i "I".</span><span class="sxs-lookup"><span data-stu-id="ee54b-108">A frequently-used variation is `System.StringComparison.OrdinalIgnoreCase`, which will match "and", "And", and "AND".</span></span> <span data-ttu-id="ee54b-109">`StringComparison.OrdinalIgnoreCase`często służy do porównywania nazw plików, nazwy ścieżek ścieżek sieciowych i inny ciąg której wartość nie ulega zmianie oparte na ustawieniach regionalnych komputera użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee54b-109">`StringComparison.OrdinalIgnoreCase` is often used to compare file names, path names, network paths, and any other string whose value does not change based on the locale of the user's computer.</span></span> <span data-ttu-id="ee54b-110">Aby uzyskać więcej informacji, zobacz <xref:System.StringComparison?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee54b-110">For more information, see <xref:System.StringComparison?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="ee54b-111">Zależne od kultury porównań są zwykle używane do porównywanie i sortowanie ciągów, które są wejściowych przez użytkowników końcowych, ponieważ znaków i konwencje sortowania ciągów te mogą się różnić w zależności od ustawień regionalnych komputera użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee54b-111">Culture-sensitive comparisons are typically used to compare and sort strings that are input by end users, because the characters and sorting conventions of these strings might vary depending on the locale of the user's computer.</span></span> <span data-ttu-id="ee54b-112">Nawet ciągów, które zawierają znaki identyczne może sortować inaczej w zależności od kultury bieżącej wątku.</span><span class="sxs-lookup"><span data-stu-id="ee54b-112">Even strings that contain identical characters might sort differently depending on the culture of the current thread.</span></span>

> [!NOTE]
> <span data-ttu-id="ee54b-113">Podczas porównywania ciągów, należy użyć metody, które jawnie określić, jakiego rodzaju porównania zamierzasz wykonać.</span><span class="sxs-lookup"><span data-stu-id="ee54b-113">When you compare strings, you should use the methods that explicitly specify what kind of comparison you intend to perform.</span></span> <span data-ttu-id="ee54b-114">Dzięki temu kodu bardziej łatwy w obsłudze i do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ee54b-114">This makes your code much more maintainable and readable.</span></span> <span data-ttu-id="ee54b-115">Jeśli to możliwe, użyj przeciążeń metody <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klas, które trwają <xref:System.StringComparison> parametru wyliczenia, dzięki czemu można określić typ porównania do wykonania.</span><span class="sxs-lookup"><span data-stu-id="ee54b-115">Whenever possible, use the overloads of the methods of the <xref:System.String?displayProperty=nameWithType> and <xref:System.Array?displayProperty=nameWithType> classes that take a <xref:System.StringComparison> enumeration parameter, so that you can specify which type of comparison to perform.</span></span> <span data-ttu-id="ee54b-116">Zaleca się unikać `==` i `!=` operatory podczas porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="ee54b-116">It is best to avoid using the `==` and `!=` operators when you compare strings.</span></span> <span data-ttu-id="ee54b-117">Ponadto należy unikać <xref:System.String.CompareTo%2A?displayProperty=nameWithType> wystąpienia metody, ponieważ brak przeciążeń <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="ee54b-117">Also, avoid using the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance methods because none of the overloads takes a <xref:System.StringComparison>.</span></span>

## <a name="example"></a><span data-ttu-id="ee54b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee54b-118">Example</span></span>

<span data-ttu-id="ee54b-119">Poniższy przykład pokazuje, jak poprawnie porównywanie ciągów, których wartości nie spowoduje zmiany oparte na ustawieniach regionalnych komputera użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee54b-119">The following example shows how to correctly compare strings whose values will not change based on the locale of the user's computer.</span></span> <span data-ttu-id="ee54b-120">Ponadto ilustruje też *interning ciąg* funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="ee54b-120">In addition, it also demonstrates the *string interning* feature of C#.</span></span> <span data-ttu-id="ee54b-121">Jeśli program deklaruje co najmniej dwa identyczne ciągu zmiennych, kompilator przechowuje je w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ee54b-121">When a program declares two or more identical string variables, the compiler stores them all in the same location.</span></span> <span data-ttu-id="ee54b-122">Wywołując <xref:System.Object.ReferenceEquals%2A> metody widać, że dwa ciągi faktycznie odwołują się do tego samego obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ee54b-122">By calling the <xref:System.Object.ReferenceEquals%2A> method, you can see that the two strings actually refer to the same object in memory.</span></span> <span data-ttu-id="ee54b-123">Użyj <xref:System.String.Copy%2A?displayProperty=nameWithType> metody w celu uniknięcia interning, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ee54b-123">Use the <xref:System.String.Copy%2A?displayProperty=nameWithType> method to avoid interning, as shown in the example.</span></span>

[!code-csharp[csProgGuideStrings#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#11)]

## <a name="example"></a><span data-ttu-id="ee54b-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee54b-124">Example</span></span>

<span data-ttu-id="ee54b-125">Poniższy przykład przedstawia sposób porównywania ciągów preferowany sposób za pomocą <xref:System.String?displayProperty=nameWithType> metod, które przyjmują <xref:System.StringComparison> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ee54b-125">The following example shows how to compare strings the preferred way by using the <xref:System.String?displayProperty=nameWithType> methods that take a <xref:System.StringComparison> enumeration.</span></span> <span data-ttu-id="ee54b-126">Należy pamiętać, że <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wystąpienia nie są używane w tym miejscu, ponieważ brak przeciążeń <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="ee54b-126">Note that the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance methods are not used here, because none of the overloads takes a <xref:System.StringComparison>.</span></span>

[!code-csharp[csProgGuideStrings#31](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#31)]

## <a name="example"></a><span data-ttu-id="ee54b-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee54b-127">Example</span></span>

<span data-ttu-id="ee54b-128">Poniższy przykład przedstawia sposób sortowanie i wyszukiwanie ciągów w tablicy w sposób zależne od kultury przy użyciu statycznych <xref:System.Array> metod, które przyjmują <xref:System.StringComparer?displayProperty=nameWithType> parametru.</span><span class="sxs-lookup"><span data-stu-id="ee54b-128">The following example shows how to sort and search for strings in an array in a culture-sensitive manner by using the static <xref:System.Array> methods that take a <xref:System.StringComparer?displayProperty=nameWithType> parameter.</span></span>

[!code-csharp[csProgGuideStrings#32](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#32)]

<span data-ttu-id="ee54b-129">Kolekcja klas takich jak <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma konstruktorów przyjmujących <xref:System.StringComparer?displayProperty=nameWithType> parametru, gdy typ elementów lub kluczy to `string`.</span><span class="sxs-lookup"><span data-stu-id="ee54b-129">Collection classes such as <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, and <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> have constructors that take a <xref:System.StringComparer?displayProperty=nameWithType> parameter when the type of the elements or keys is `string`.</span></span> <span data-ttu-id="ee54b-130">Ogólnie rzecz biorąc, należy te konstruktorów w miarę możliwości używać i określ `Ordinal` lub `OrdinalIgnoreCase`.</span><span class="sxs-lookup"><span data-stu-id="ee54b-130">In general, you should use these constructors whenever possible, and specify either `Ordinal` or `OrdinalIgnoreCase`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee54b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee54b-131">See also</span></span>
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [<span data-ttu-id="ee54b-132">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ee54b-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="ee54b-133">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="ee54b-133">Comparing Strings</span></span>](../../../standard/base-types/comparing.md)  
 [<span data-ttu-id="ee54b-134">Globalizacja i lokalizacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="ee54b-134">Globalizing and Localizing Applications</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)