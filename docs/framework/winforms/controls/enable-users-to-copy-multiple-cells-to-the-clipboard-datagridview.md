---
title: "Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows"
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
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 703284572005ab262a7e9379b601d8144d8e9af1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="94d12-102">Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94d12-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="94d12-103">Po włączeniu kopiowanie komórki wprowadzeniu danych w sieci <xref:System.Windows.Forms.DataGridView> łatwo dostępne dla innych aplikacji za pomocą formantu <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="94d12-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="94d12-104">Wartości zaznaczonych komórek są konwertowane na ciągi i dodane do Schowka jako wartości tekstowe tabulacji wklejania w aplikacjach, takich jak Notatnik, a program Excel, a w formacie HTML tabeli wklejania w aplikacjach, takich jak Word.</span><span class="sxs-lookup"><span data-stu-id="94d12-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="94d12-105">Można skonfigurować komórki kopiowanie skopiować tylko wartości komórek, zawierają tekst nagłówka wiersza i kolumny w danych ze Schowka lub zawierają tekst nagłówka, tylko wtedy, gdy użytkownicy wybierają całego wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="94d12-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="94d12-106">W zależności od trybu wyboru użytkownicy mogą wybierać wielu grup odłączonego komórek.</span><span class="sxs-lookup"><span data-stu-id="94d12-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="94d12-107">Gdy użytkownik kopiuje komórek do Schowka, wierszy i kolumn z nie zaznaczone komórki nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="94d12-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="94d12-108">Wszystkie inne wierszy lub kolumn stają się wierszy i kolumn w tabeli danych skopiowany do Schowka.</span><span class="sxs-lookup"><span data-stu-id="94d12-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="94d12-109">Niezaznaczone komórek w tych wierszy lub kolumn są kopiowane jako puste elementy zastępcze do Schowka.</span><span class="sxs-lookup"><span data-stu-id="94d12-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="94d12-110">Aby umożliwić kopiowanie komórki</span><span class="sxs-lookup"><span data-stu-id="94d12-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="94d12-111">Ustaw <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="94d12-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="94d12-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="94d12-112">Example</span></span>  
 <span data-ttu-id="94d12-113">W poniższym przykładzie kompletny kod pokazano, jak komórki są kopiowane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="94d12-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="94d12-114">Ten przykład zawiera przycisk, który kopiuje zaznaczonych komórek do Schowka przy użyciu <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> — metoda i wyświetla zawartość Schowka w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="94d12-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94d12-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="94d12-115">Compiling the Code</span></span>  
 <span data-ttu-id="94d12-116">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="94d12-116">This code requires:</span></span>  
  
-   <span data-ttu-id="94d12-117">Odwołania do zestawów N:System i N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="94d12-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="94d12-118">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94d12-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="94d12-119">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="94d12-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="94d12-120">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="94d12-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d12-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94d12-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [<span data-ttu-id="94d12-122">Wybór i używanie Schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94d12-122">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)