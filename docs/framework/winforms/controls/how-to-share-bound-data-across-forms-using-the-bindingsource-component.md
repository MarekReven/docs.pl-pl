---
title: "Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource"
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
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95fd7583e6d86aa84c53f6cee7056f1d631e948b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="28e3a-102">Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="28e3a-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="28e3a-103">Dane można łatwo udostępniać wielu formularzach za pomocą <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="28e3a-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="28e3a-104">Na przykład można wyświetlić jeden formularz tylko do odczytu, który znajduje się podsumowanie danych źródła danych oraz innej formy można edytować, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="28e3a-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="28e3a-105">W tym przykładzie pokazano, w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="28e3a-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e3a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="28e3a-106">Example</span></span>  
 <span data-ttu-id="28e3a-107">W poniższym przykładzie pokazano, jak udostępnić <xref:System.Windows.Forms.BindingSource> i jego danych powiązanych w wielu formularzach.</span><span class="sxs-lookup"><span data-stu-id="28e3a-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="28e3a-108">W tym przykładzie udostępnionego <xref:System.Windows.Forms.BindingSource> jest przekazany do konstruktora formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="28e3a-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="28e3a-109">Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.</span><span class="sxs-lookup"><span data-stu-id="28e3a-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28e3a-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenia dla <xref:System.Windows.Forms.BindingSource> składnika jest obsługiwany w tym przykładzie, aby upewnić się, że dwa formularze pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="28e3a-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="28e3a-111">Aby uzyskać więcej informacji na temat przyczyn jest to zrobić, zobacz [porady: Upewnij się, wiele formanty powiązane z tym samym dane źródła pozostają zsynchronizowane](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="28e3a-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28e3a-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="28e3a-112">Compiling the Code</span></span>  
 <span data-ttu-id="28e3a-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="28e3a-113">This example requires:</span></span>  
  
-   <span data-ttu-id="28e3a-114">Odwołania do zestawów systemu, System.Windows.Forms System.Drawing, dane systemowe i zestawów System.Xml.</span><span class="sxs-lookup"><span data-stu-id="28e3a-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="28e3a-115">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="28e3a-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="28e3a-116">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="28e3a-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="28e3a-117">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="28e3a-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e3a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28e3a-118">See Also</span></span>  
 [<span data-ttu-id="28e3a-119">BindingSource — składnik</span><span class="sxs-lookup"><span data-stu-id="28e3a-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="28e3a-120">Powiązanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28e3a-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="28e3a-121">Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="28e3a-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)