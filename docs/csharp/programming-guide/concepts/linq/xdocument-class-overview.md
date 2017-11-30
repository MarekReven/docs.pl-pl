---
title: "Przegląd klasy XDocument (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dcb221dadcae934c382d20a2a93149af9541db9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="0d030-102">Przegląd klasy XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="0d030-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="0d030-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d030-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="0d030-104">Przegląd klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="0d030-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="0d030-105"><xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0d030-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="0d030-106">W tym deklaracja XML przetwarzania instrukcje i komentarze.</span><span class="sxs-lookup"><span data-stu-id="0d030-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="0d030-107">Należy pamiętać, że należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli są wymagane określone funkcje udostępniane przez <xref:System.Xml.Linq.XDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d030-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="0d030-108">W wielu sytuacjach może współpracować bezpośrednio z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0d030-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0d030-109">Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostszy model programowania.</span><span class="sxs-lookup"><span data-stu-id="0d030-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="0d030-110"><xref:System.Xml.Linq.XDocument>pochodną <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="0d030-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="0d030-111">W związku z tym może zawierać węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0d030-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="0d030-112">Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden element podrzędny <xref:System.Xml.Linq.XElement> węzła.</span><span class="sxs-lookup"><span data-stu-id="0d030-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="0d030-113">Ta właściwość odzwierciedla standardu XML, że może istnieć tylko jeden element główny dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0d030-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="0d030-114">Składniki XDocument</span><span class="sxs-lookup"><span data-stu-id="0d030-114">Components of XDocument</span></span>  
 <span data-ttu-id="0d030-115"><xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0d030-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="0d030-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d030-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="0d030-117"><xref:System.Xml.Linq.XDeclaration>Umożliwia określenie odpowiednich części deklaracji XML: Wersja XML, kodowania dokumentu, oraz czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="0d030-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="0d030-118">Jeden <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d030-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="0d030-119">To jest węzeł główny dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0d030-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="0d030-120">Dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d030-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="0d030-121">Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.</span><span class="sxs-lookup"><span data-stu-id="0d030-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="0d030-122">Dowolną liczbę <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d030-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="0d030-123">Komentarze będzie elementów równorzędnych do elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="0d030-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="0d030-124"><xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszego argumentu na liście, ponieważ nie jest prawidłowa dla dokumentu XML można uruchomić w komentarzu.</span><span class="sxs-lookup"><span data-stu-id="0d030-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="0d030-125">Jeden <xref:System.Xml.Linq.XDocumentType> dla definicji DTD.</span><span class="sxs-lookup"><span data-stu-id="0d030-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="0d030-126">Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą miały deklaracja XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` ustawioną `false` (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0d030-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="0d030-127">Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawienie wersji "1.0", a kodowanie "utf-8".</span><span class="sxs-lookup"><span data-stu-id="0d030-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="0d030-128">Przy użyciu klasy XElement bez klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="0d030-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="0d030-129">Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasy jest główna klasa w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania.</span><span class="sxs-lookup"><span data-stu-id="0d030-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="0d030-130">W wielu przypadkach aplikacji nie będzie wymagać tworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0d030-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="0d030-131">Za pomocą <xref:System.Xml.Linq.XElement> klasy, można Utwórz drzewo XML, Dodaj do niej inne drzewa XML, zmodyfikuj drzewa XML i zapisz go.</span><span class="sxs-lookup"><span data-stu-id="0d030-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="0d030-132">Przy użyciu klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="0d030-132">Using XDocument</span></span>  
 <span data-ttu-id="0d030-133">Aby utworzyć <xref:System.Xml.Linq.XDocument>, użyj konstrukcji funkcjonalności, tak samo, jak należy utworzyć <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d030-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="0d030-134">Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i jego skojarzony zawarte obiekty.</span><span class="sxs-lookup"><span data-stu-id="0d030-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="0d030-135">Po sprawdzeniu test.xml plików można uzyskać następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0d030-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d030-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d030-136">See Also</span></span>  
 [<span data-ttu-id="0d030-137">LINQ do XML-przegląd programowania w języku (C#)</span><span class="sxs-lookup"><span data-stu-id="0d030-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)