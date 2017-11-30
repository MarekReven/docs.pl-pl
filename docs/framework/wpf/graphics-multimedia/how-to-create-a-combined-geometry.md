---
title: "Jak tworzyć połączone geometrie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2be0471f27d26b145cc29847a08bf3bc3b1d51ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="8ac3b-102">Jak tworzyć połączone geometrie</span><span class="sxs-lookup"><span data-stu-id="8ac3b-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="8ac3b-103">Ten przykład przedstawia sposób łączenia mają geometrię.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="8ac3b-104">Aby połączyć dwie mają geometrię, należy użyć <xref:System.Windows.Media.CombinedGeometry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="8ac3b-105">Ustaw jego <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> właściwości z dwóch geometrii, łączenie i ustawić <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> właściwość, która określa, jak mają geometrię zostaną połączone ze sobą, aby `Union`, `Intersect`, `Exclude`, lub `Xor`.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="8ac3b-106">Aby utworzyć geometrii złożonego z dwóch lub więcej mają geometrię, użyj <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ac3b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ac3b-107">Example</span></span>  
 <span data-ttu-id="8ac3b-108">W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia geometrii z `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="8ac3b-109">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="8ac3b-110">![Wyłącz wyniki użycia trybu łączenia](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="8ac3b-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="8ac3b-111">Wyklucz geometrii połączone</span><span class="sxs-lookup"><span data-stu-id="8ac3b-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="8ac3b-112">W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="8ac3b-113">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="8ac3b-114">![Wyniki INTERSECT połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="8ac3b-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="8ac3b-115">Łączna geometrii Intersect</span><span class="sxs-lookup"><span data-stu-id="8ac3b-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="8ac3b-116">W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Union`.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="8ac3b-117">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="8ac3b-118">![Wyniki Unii połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="8ac3b-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="8ac3b-119">Łączna geometrii Unii</span><span class="sxs-lookup"><span data-stu-id="8ac3b-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="8ac3b-120">W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Xor`.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="8ac3b-121">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.</span><span class="sxs-lookup"><span data-stu-id="8ac3b-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="8ac3b-122">![Wyniki Xor połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="8ac3b-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="8ac3b-123">Xor geometrii połączone</span><span class="sxs-lookup"><span data-stu-id="8ac3b-123">Combined Geometry Xor</span></span>