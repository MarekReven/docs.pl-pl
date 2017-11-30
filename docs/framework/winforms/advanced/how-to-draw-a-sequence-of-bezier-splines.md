---
title: 'Porady: Rysowanie sekwencji B &#233; zier krzywe'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76a0ab96f40c1b8d9db6f61d19ece82066b63eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="7f6df-102">Porady: Rysowanie sekwencji B &#233; zier krzywe</span><span class="sxs-lookup"><span data-stu-id="7f6df-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="7f6df-103">Można użyć <xref:System.Drawing.Graphics.DrawBeziers%2A> metody <xref:System.Drawing.Graphics> klasy Rysowanie sekwencji połączone krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="7f6df-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f6df-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f6df-104">Example</span></span>  
 <span data-ttu-id="7f6df-105">Poniższy przykład rysuje krzywą, która składa się z dwóch połączonych krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="7f6df-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="7f6df-106">Punkt końcowy pierwszego krzywej Beziera jest punkt początkowy drugiego krzywej Beziera.</span><span class="sxs-lookup"><span data-stu-id="7f6df-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="7f6df-107">Na poniższej ilustracji przedstawiono połączonych krzywe wraz z siedmiu punktów.</span><span class="sxs-lookup"><span data-stu-id="7f6df-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="7f6df-108">![Beziera krzywej składanej](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="7f6df-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f6df-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7f6df-109">Compiling the Code</span></span>  
 <span data-ttu-id="7f6df-110">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f6df-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f6df-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f6df-111">See Also</span></span>  
 [<span data-ttu-id="7f6df-112">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7f6df-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="7f6df-113">Krzywe Beziera w GDI +</span><span class="sxs-lookup"><span data-stu-id="7f6df-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="7f6df-114">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="7f6df-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)