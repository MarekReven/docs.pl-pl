---
title: "x:ClassModifier — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: "22"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 111c4a6ed78a908ae3b171dc9349a3c9b81750de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="5cc4c-102">x:ClassModifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="5cc4c-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="5cc4c-103">Modyfikuje zachowanie kompilacji XAML podczas `x:Class` jest również udostępniany.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="5cc4c-104">W szczególności, zamiast tworzyć częściowym `class` mający `Public` (ustawienie domyślne), poziom dostępu dostarczonego `x:Class` jest tworzony z `NotPublic` poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="5cc4c-105">Dotyczy to poziom dostępu dla tej klasy w wygenerowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5cc4c-106">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5cc4c-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5cc4c-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="5cc4c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cc4c-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="5cc4c-108">*NotPublic*</span></span>|<span data-ttu-id="5cc4c-109">Dokładnie taki ciąg znaków do przekazania do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> może być różna w zależności od używanej język programowania związane z kodem.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="5cc4c-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="5cc4c-111">Zależności</span><span class="sxs-lookup"><span data-stu-id="5cc4c-111">Dependencies</span></span>  
 <span data-ttu-id="5cc4c-112">[x: Class](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także w tym samym elemencie, a ten element musi być elementem głównym na stronie.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="5cc4c-113">Aby uzyskać więcej informacji, zobacz [ \[MS XAML\] sekcji 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="5cc4c-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc4c-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cc4c-114">Remarks</span></span>  
 <span data-ttu-id="5cc4c-115">Wartość `x:ClassModifier` w usługach programu .NET Framework XAML użycia zależy od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="5cc4c-116">Ciąg do użycia zależy od tego, jak implementuje każdego języka jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu zwraca do definiowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, oraz czy ten język jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="5cc4c-117">Aby uzyskać [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `internal`.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-117">For [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="5cc4c-118">Aby uzyskać [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `Friend`.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-118">For [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="5cc4c-119">Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], żadne obiekty docelowe istnieje obsługujące kompilacji XAML; w związku z tym wartość do przekazania jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="5cc4c-120">Można również określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` w [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` w [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]), jednak określenie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> rzadko jest wykonywana, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> już jest zachowaniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="5cc4c-121">Inne wartości z kodu użytkownika równoważne poziomu dostępu do ograniczenia, takie jak `private` w [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], nie są odpowiednie dla `x:ClassModifier` odwołania zagnieżdżona klasa nie są obsługiwane w języku XAML i w związku z tym <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modyfikator ma takie same efekt.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-121">Other values with equivalent user code access-level restrictions, such as `private` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="5cc4c-122">Uwagi dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5cc4c-122">Security Notes</span></span>  
 <span data-ttu-id="5cc4c-123">Poziom dostępu, zgodnie z deklaracją w `x:ClassModifier` nadal podlega interpretacji przez konkretnego struktur i ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="5cc4c-124">WPF zawiera funkcje do ładowania i utworzyć wystąpienia typów gdzie `x:ClassModifier` jest `internal`, jeśli z za pomocą pakietu odwołanie do identyfikatora URI zasobu WPF odwołuje się do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="5cc4c-125">W wyniku tego przypadku i potencjalnie innych podoba Ci się implementowane przez innych platform, nie należy polegać wyłącznie na `x:ClassModifier` Aby zablokować wszystkie możliwe podczas tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc4c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cc4c-126">See Also</span></span>  
 [<span data-ttu-id="5cc4c-127">x: Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="5cc4c-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="5cc4c-128">Związane z kodem i języka XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="5cc4c-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="5cc4c-129">x: fieldmodifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="5cc4c-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="5cc4c-130">Zabezpieczenia (WPF)</span><span class="sxs-lookup"><span data-stu-id="5cc4c-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="5cc4c-131">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="5cc4c-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)