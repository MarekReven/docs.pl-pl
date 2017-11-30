---
title: "Wskazówki: utwórz niestandardowy przycisk animowany"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bce1140ed11332b5bf30d487b2acacc644687d26
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="52b35-102">Wskazówki: utwórz niestandardowy przycisk animowany</span><span class="sxs-lookup"><span data-stu-id="52b35-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="52b35-103">Zgodnie z sugestią, jego nazwa, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] stanowi doskonałe rozwiązanie do tworzenia środowiska sformatowanego prezentacji dla klientów.</span><span class="sxs-lookup"><span data-stu-id="52b35-103">As its name suggests, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="52b35-104">Te wskazówki pokazują, jak dostosować wygląd i zachowanie przycisku (w tym animacji).</span><span class="sxs-lookup"><span data-stu-id="52b35-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="52b35-105">Takie dostosowanie odbywa się przy użyciu stylu i szablonu, dzięki czemu można zastosować tego przycisku niestandardowego łatwe do dowolnego przycisków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b35-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="52b35-106">Na poniższej ilustracji przedstawiono dostosowany przycisk zostanie utworzenie.</span><span class="sxs-lookup"><span data-stu-id="52b35-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="52b35-107">![Dostosowany przycisk, który spowoduje utworzenie](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="52b35-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="52b35-108">Grafika wektorowa, które tworzą wygląd przycisku są tworzone za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52b35-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="52b35-109">z wyjątkiem jest bardziej zaawansowany i rozszerzalny jest podobny do formatu HTML.</span><span class="sxs-lookup"><span data-stu-id="52b35-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="52b35-110">można wpisać w ręcznie przy użyciu programu Microsoft Visual Studio lub Notatnik, lub można użyć narzędzia projektowe visual takich jak Microsoft Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="52b35-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="52b35-111">Expression Blend polega na tworzeniu podstawowych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod, więc obie metody tworzenia tej samej grafiki.</span><span class="sxs-lookup"><span data-stu-id="52b35-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52b35-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52b35-112">In This Section</span></span>  
 [<span data-ttu-id="52b35-113">Utwórz przycisk przy użyciu programu Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="52b35-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="52b35-114">Przedstawia sposób tworzenia przycisków z zachowaniem niestandardowych za pomocą projektanta funkcji Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="52b35-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="52b35-115">Utwórz przycisk przy użyciu języka XAML</span><span class="sxs-lookup"><span data-stu-id="52b35-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="52b35-116">Przedstawia sposób tworzenia przycisków z zachowaniem niestandardowych za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52b35-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52b35-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="52b35-117">Related Sections</span></span>  
 [<span data-ttu-id="52b35-118">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="52b35-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="52b35-119">W tym artykule opisano, jak szablony i style może służyć do określenia wygląd i zachowanie kontroli.</span><span class="sxs-lookup"><span data-stu-id="52b35-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="52b35-120">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="52b35-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="52b35-121">W tym artykule opisano, jak można animować obiektów przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animacji i czasu systemu.</span><span class="sxs-lookup"><span data-stu-id="52b35-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="52b35-122">Malowanie pełnych kolorów i gradientów — omówienie</span><span class="sxs-lookup"><span data-stu-id="52b35-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="52b35-123">Informacje dotyczące używania obiektów pędzla do rysowania z kolorami, gradienty liniowe i gradientu promieniowego.</span><span class="sxs-lookup"><span data-stu-id="52b35-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="52b35-124">Omówienie skutków mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="52b35-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="52b35-125">Opisuje skutki mapy bitowej obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i objaśnienie sposobu ich zastosowania.</span><span class="sxs-lookup"><span data-stu-id="52b35-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>