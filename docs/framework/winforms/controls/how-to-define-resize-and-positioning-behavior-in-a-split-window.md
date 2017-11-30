---
title: "Porady: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie"
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
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db4a99c7dae7783e8ea51f43ad51fcd2214997e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="6ecae-102">Porady: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="6ecae-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="6ecae-103">Panele <xref:System.Windows.Forms.SplitContainer> kontroli redagowanie również są zmiany rozmiaru i manipulowanie przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6ecae-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="6ecae-104">Jednak zostanie wystąpić sytuacje, kiedy można programowo zarządzać rozdzielacza, gdzie jest umieszczony i w jakim stopniu można go przenieść.</span><span class="sxs-lookup"><span data-stu-id="6ecae-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="6ecae-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwości i innych właściwości w <xref:System.Windows.Forms.SplitContainer> kontroli zapewniają precyzyjną kontrolę zachowania interfejsu użytkownika w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="6ecae-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="6ecae-106">W poniższej tabeli przedstawiono te właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ecae-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="6ecae-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6ecae-107">Name</span></span>|<span data-ttu-id="6ecae-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6ecae-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6ecae-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="6ecae-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="6ecae-110">Określa, czy rozdzielacz jest ruchomy za pomocą klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="6ecae-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="6ecae-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="6ecae-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="6ecae-112">Określa odległość w pikselach pasek podziału ruchomy od lewej lub górnej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="6ecae-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="6ecae-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="6ecae-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="6ecae-114">Określa minimalny odstęp w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6ecae-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="6ecae-115">W poniższym przykładzie modyfikuje <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwości do utworzenia efektu "przyciąganie podziału"; gdy użytkownik przeciąga rozdzielacza, zwiększa narastająco w jednostkach 10 pikseli zamiast domyślnego 1.</span><span class="sxs-lookup"><span data-stu-id="6ecae-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="6ecae-116">Aby określić zachowanie podczas zmiany rozmiaru SplitContainer</span><span class="sxs-lookup"><span data-stu-id="6ecae-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="6ecae-117">W procedurze, ustaw <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwości do żądanego rozmiaru, dzięki czemu zostaje przywrócony zachowanie "przyciąganie" rozdzielacza.</span><span class="sxs-lookup"><span data-stu-id="6ecae-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="6ecae-118">W poniższym przykładzie kodu, w ramach formularza <xref:System.Windows.Forms.Form.Load> zdarzenie, podziału w <xref:System.Windows.Forms.SplitContainer> kontrola została ustawiona na przejście 10 pikseli podczas przeciągania.</span><span class="sxs-lookup"><span data-stu-id="6ecae-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="6ecae-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6ecae-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="6ecae-120">Przenoszenie rozdzielacza nieco do lewej lub prawej nie wpłyną zauważalny; Gdy wskaźnik myszy przechodzi 10 pikseli, rozdzielacza spowoduje przyciąganie do nowej pozycji.</span><span class="sxs-lookup"><span data-stu-id="6ecae-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ecae-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ecae-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>