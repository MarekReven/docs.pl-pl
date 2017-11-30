---
title: "Margines i wypełnienie w formantach formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d8a73963a8f9f1e3d8b80b6c16f189e0221c55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="055d1-102">Margines i wypełnienie w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="055d1-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="055d1-103">Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="055d1-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="055d1-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw zapewnia wiele funkcji układu, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="055d1-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="055d1-105">Dwie najważniejsze to <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="055d1-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="055d1-106"><xref:System.Windows.Forms.Control.Margin%2A> Właściwość definiuje obszar wokół formantu, czy przechowuje inne formanty w określonej odległości od obramowania formantu.</span><span class="sxs-lookup"><span data-stu-id="055d1-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="055d1-107"><xref:System.Windows.Forms.Control.Padding%2A> Właściwość definiuje miejsce wewnątrz kontrolkę, która zachowuje zawartość formantu (na przykład wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości) w określonej odległości od obramowania formantu.</span><span class="sxs-lookup"><span data-stu-id="055d1-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="055d1-108">Na poniższej ilustracji pokazano <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="055d1-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="055d1-109">![Formanty formularzy dopełnienia i marginesów dla systemu Windows](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="055d1-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="055d1-110">Brak obsługi tej funkcji w programie Visual Studio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="055d1-110">There is design-time support for this feature in Visual Studio.</span></span>  <span data-ttu-id="055d1-111">Zobacz też [wskazówki: tworzenie limit formantów formularzy systemu Windows z dopełnienie, marginesami oraz właściwościami AutoSize właściwość](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="055d1-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055d1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="055d1-112">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>