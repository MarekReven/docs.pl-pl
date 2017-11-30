---
title: "Jak utworzyć schemat tekstu"
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
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76d0dcf63f9d8a66106f4bcdc52a2bf98c75cdc4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="5e122-102">Jak utworzyć schemat tekstu</span><span class="sxs-lookup"><span data-stu-id="5e122-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="5e122-103">W większości przypadków, gdy dodajesz ornamentacji do ciągów tekstowych w Twojej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, w przypadku używania tekstu pod względem zbiór znaków discrete lub symboli.</span><span class="sxs-lookup"><span data-stu-id="5e122-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="5e122-104">Na przykład można utworzyć pędzla gradientu liniowego i zastosować je do <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.TextBox> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e122-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="5e122-105">Podczas wyświetlania lub edytowania pola tekstowego, pędzla gradientu liniowego jest automatycznie stosowana w bieżącym zestawie znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5e122-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="5e122-106">![Tekst wyświetlany przy użyciu pędzla gradientu liniowego](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="5e122-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="5e122-107">Przykład pędzla gradientu liniowego stosowane do pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="5e122-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="5e122-108">Jednak możesz również przeprowadzić konwersję tekstu do <xref:System.Windows.Media.Geometry> obiektów, pozwala na tworzenie innych typów wizualnie RTF.</span><span class="sxs-lookup"><span data-stu-id="5e122-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="5e122-109">Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konturu ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="5e122-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="5e122-110">![Używanie pędzla gradientu liniowego konspektu tekstu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="5e122-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="5e122-111">Przykład pędzla gradientu liniowego stosowane do geometrii konspektu tekstu</span><span class="sxs-lookup"><span data-stu-id="5e122-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="5e122-112">Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu, nie jest już zbiór znaków — nie można zmodyfikować znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5e122-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="5e122-113">Jednak może wpływać na wygląd tekst skonwertowany zmieniając jej obrysu i wypełnienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e122-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="5e122-114">Obrysu odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="5e122-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="5e122-115">Poniższe przykłady przedstawiają kilka sposobów tworzenia efekty wizualne, modyfikując obrysu i wypełnienia przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="5e122-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="5e122-116">![Tekst z różnymi kolorami wypełnienia i pociągnięcia](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="5e122-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="5e122-117">Przykładowa konfiguracja obrysu i wypełnienia do różnych kolorów</span><span class="sxs-lookup"><span data-stu-id="5e122-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="5e122-118">![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="5e122-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="5e122-119">Przykład pędzel obrazu na obrysu</span><span class="sxs-lookup"><span data-stu-id="5e122-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="5e122-120">Istnieje również możliwość modyfikowania obwiedni prostokąta pola lub wyróżnianie tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="5e122-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="5e122-121">Poniższy przykład przedstawia sposób tworzenia efekty wizualne, modyfikując obrysu i wyróżnianie tekstu przekonwertowany.</span><span class="sxs-lookup"><span data-stu-id="5e122-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="5e122-122">![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="5e122-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="5e122-123">Przykład pędzel obrazu na obrysu i wyróżnienia</span><span class="sxs-lookup"><span data-stu-id="5e122-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e122-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e122-124">Example</span></span>  
 <span data-ttu-id="5e122-125">Klucz do konwersji tekstu do <xref:System.Windows.Media.Geometry> obiektu jest użycie <xref:System.Windows.Media.FormattedText> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e122-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="5e122-126">Po utworzeniu tego obiektu można używać <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> i <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metod można przekonwertować na tekst, który <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5e122-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="5e122-127">Pierwsza metoda zwraca geometrii tekst sformatowany; Druga metoda zwraca obwiedni geometrii tekst sformatowany.</span><span class="sxs-lookup"><span data-stu-id="5e122-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="5e122-128">W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i pobrać mają geometrię tekst sformatowany i jego pola ograniczającego.</span><span class="sxs-lookup"><span data-stu-id="5e122-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="5e122-129">Aby wyświetlić pobranej <xref:System.Windows.Media.Geometry> obiekty, musisz mieć dostęp <xref:System.Windows.Media.DrawingContext> obiektu, w którym jest wyświetlany tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="5e122-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="5e122-130">W tym przykładzie kodu polega to na tworzenie obiektu kontrolki niestandardowej pochodzącej z klasy, która obsługuje renderowanie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e122-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="5e122-131">Aby wyświetlić <xref:System.Windows.Media.Geometry> obiektów w kontrolki niestandardowej, podaj zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5e122-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="5e122-132">Należy używać przesłoniętą metodę <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metodę, by narysować <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5e122-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="5e122-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e122-133">See Also</span></span>  
 [<span data-ttu-id="5e122-134">Rysowanie sformatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="5e122-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)