---
title: "Jak animować położenie obiektu z wykorzystaniem PointAnimation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6590c79ac6b6f104d9944a32da4c99318d334eec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="08036-102">Jak animować położenie obiektu z wykorzystaniem PointAnimation</span><span class="sxs-lookup"><span data-stu-id="08036-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="08036-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.PointAnimation> klasy do animowania obiektu wzdłuż <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="08036-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08036-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="08036-104">Example</span></span>  
 <span data-ttu-id="08036-105">Poniższy przykład przenosi elipsy <xref:System.Windows.Shapes.Path> z jednego miejsca na ekranie do innego.</span><span class="sxs-lookup"><span data-stu-id="08036-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="08036-106">Przykład animuje pozycja <xref:System.Windows.Media.EllipseGeometry> za pomocą <xref:System.Windows.Media.Animation.PointAnimation> do animowania <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="08036-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="08036-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08036-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="08036-108">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="08036-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="08036-109">Grafika i Multimedia</span><span class="sxs-lookup"><span data-stu-id="08036-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="08036-110">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="08036-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="08036-111">Synchronizację</span><span class="sxs-lookup"><span data-stu-id="08036-111">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="08036-112">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="08036-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)