---
title: "Porady: przycinanie i skalowanie obrazów"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb5d527cd1047197f370c4a9a9b1f8f33461653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="99405-102">Porady: przycinanie i skalowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="99405-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="99405-103"><xref:System.Drawing.Graphics> Klasa udostępnia kilka <xref:System.Drawing.Graphics.DrawImage%2A> metod, niektóre z nich ma parametry prostokąt źródłowych i docelowych, które umożliwia przycinanie i skalowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="99405-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99405-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="99405-104">Example</span></span>  
 <span data-ttu-id="99405-105">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu z dysku Apple.gif.</span><span class="sxs-lookup"><span data-stu-id="99405-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="99405-106">Kod rysuje obraz całej firmy apple w jego oryginalny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="99405-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="99405-107">Kod wywołuje <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu do rysowania część obrazu firmy apple w prostokącie docelowego, który jest większy niż oryginalny obraz firmy apple.</span><span class="sxs-lookup"><span data-stu-id="99405-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="99405-108"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, która część firmy apple do rysowania analizując prostokąta źródła jest określona przez trzecią, czwarty, argumenty piątego i szóstego.</span><span class="sxs-lookup"><span data-stu-id="99405-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="99405-109">W takim przypadku przycięcia 75 procent szerokości i wysokości 75 procent firmy apple.</span><span class="sxs-lookup"><span data-stu-id="99405-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="99405-110"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, gdzie do rysowania przycięte firmy apple i jak duży, aby wprowadzić przycięte apple analizując docelowy prostokąt, czyli drugiego argumentu.</span><span class="sxs-lookup"><span data-stu-id="99405-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="99405-111">W takim przypadku prostokąt docelowy jest 30 procent szersze i 30 procent wyższe niż oryginalnego obrazu.</span><span class="sxs-lookup"><span data-stu-id="99405-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="99405-112">Na poniższej ilustracji przedstawiono oryginalne firmy apple i skalowana, przycięte firmy apple.</span><span class="sxs-lookup"><span data-stu-id="99405-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="99405-113">![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="99405-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99405-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="99405-114">Compiling the Code</span></span>  
 <span data-ttu-id="99405-115">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99405-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="99405-116">Upewnij się zastąpić `Apple.gif` nazwę pliku obrazu oraz ścieżki, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="99405-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99405-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99405-117">See Also</span></span>  
 [<span data-ttu-id="99405-118">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="99405-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="99405-119">Praca z obrazami, mapami bitowymi, ikony i metapliki</span><span class="sxs-lookup"><span data-stu-id="99405-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)