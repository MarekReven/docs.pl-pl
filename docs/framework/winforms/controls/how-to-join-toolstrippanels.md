---
title: "Porady: łączenie ToolStripPanels"
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
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d77d29526656da0c149ee4b8e940f4ad9e87ca3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="5901b-102">Porady: łączenie ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="5901b-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="5901b-103">Możesz także dołączyć do <xref:System.Windows.Forms.ToolStrip> formanty <xref:System.Windows.Forms.ToolStripPanel> w czasie wykonywania, która zapewnia elastyczność aplikacje interfejsu wielu dokumentów (MDI).</span><span class="sxs-lookup"><span data-stu-id="5901b-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5901b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5901b-104">Example</span></span>  
 <span data-ttu-id="5901b-105">Poniższy przykład kodu pokazuje, jak sprzęgać <xref:System.Windows.Forms.ToolStrip> formanty <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="5901b-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5901b-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5901b-106">Compiling the Code</span></span>  
 <span data-ttu-id="5901b-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5901b-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5901b-108">Odwołania do zestawów System.Design, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5901b-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5901b-109">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5901b-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5901b-110">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5901b-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5901b-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5901b-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5901b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5901b-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="5901b-113">Porady: używanie elementu ToolStripPanels dla MDI</span><span class="sxs-lookup"><span data-stu-id="5901b-113">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)