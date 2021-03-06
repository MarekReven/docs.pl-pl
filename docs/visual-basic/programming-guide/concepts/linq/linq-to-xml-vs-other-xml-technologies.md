---
title: LINQ do XML programu vs. Inne Technologies2 XML
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba342b68828d427bfbddf51fa3d2da5d3c614dae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ do XML programu vs. Inne technologie XML
W tym temacie porównuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] następujące technologie XML: <xref:System.Xml.XmlReader>, XSLT, MSXML i XmlLite. Te informacje mogą pomóc w określeniu technologii.  
  
 Porównanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do modelu DOM (Document Object), zobacz [LINQ do XML programu vs. Modelu DOM (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ do XML programu vs. Element XmlReader  
 <xref:System.Xml.XmlReader>jest szybkie, tylko do przodu, buforowanie analizatora składni.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zaimplementowano nad <xref:System.Xml.XmlReader>, i są ściśle powiązane. Jednak umożliwia także <xref:System.Xml.XmlReader> przez samego siebie.  
  
 Na przykład załóżmy, że są tworzenia usługi sieci Web analizy setki dokumentów XML na sekundę i dokumenty ma taką samą strukturę, co oznacza, że masz zapisu jedna implementacja kodu do analizy kodu XML. W takim przypadku będzie prawdopodobnie chcesz użyć <xref:System.Xml.XmlReader> przez samego siebie.  
  
 Z kolei, jeśli tworzysz system analizuje dużo mniejsze dokumentów XML i każdej z nich jest inny, czy chcesz korzystając z usprawnień wydajności który [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ do XML programu vs. XSLT  
 Zarówno [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i XSLT zapewniają szeroką gamę możliwości transformacji dokumentów XML. XSLT jest oparty na regułach, deklaratywny podejściem. Zaawansowane XSLT programistów zapisu XSLT w stylu programowania funkcjonalności który wyróżniane bezstanowych podejście. Przekształcenia można pisać przy użyciu czystych funkcji, które są implementowane bez efekty uboczne. Takie podejście reguły lub funkcjonalności nieznany wielu deweloperów i może być trudny i czasochłonny dowiedzieć się więcej.  
  
 XSLT może być bardzo wydajni systemu, który daje skalowalnych aplikacji wysokiej wydajności. Na przykład niektóre duże sieci Web firmy użyć XSLT jako sposób generowania kodu HTML z pliku XML, który został pobierane z różnych magazynów danych. Aparatu zarządzanego XSLT kompiluje XSLT do kodu CLR, a nawet lepszą w niektórych scenariuszach niż silnik natywny XSLT.  
  
 Jednak XSLT nie korzystać z wiedzy C# i Visual Basic, które mają wielu deweloperów. Wymaga to deweloperom pisanie kodu w języku programowania różnych i złożoności. Przy użyciu dwóch — zintegrowane programowanie systemów, takich jak C# (lub Visual Basic) i XSLT wyniki w systemach oprogramowania, które są trudne do opracowywania i obsługa.  
  
 Po opanowaniu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wyrażenia, zapytań [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przekształceń są zaawansowanych technologii, która jest łatwy w użyciu. Zasadniczo formowania dokument XML przy użyciu konstrukcji funkcjonalności ściąganie danych z różnych źródeł, konstruowania <xref:System.Xml.Linq.XElement> dynamicznie obiekty i zebrania całego w nowym drzewie XML. Transformacja mogą generować całkowicie nowy dokument. Konstruowanie przekształcenia w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest względnie proste i intuicyjne, a wynikowy kod jest możliwy do odczytu. Pozwala to ograniczyć koszty rozwoju i konserwacji.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie ma zastąpić XSLT. XSLT jest nadal narzędzie ulubionym skomplikowane i zorientowany transformacji XML, zwłaszcza, jeśli nie zdefiniowano także strukturę dokumentu.  
  
 Zaletą jest konsorcjum World Wide Web (W3C) standardowy jest XSLT. Jeśli masz wymagane użycie tylko technologii, które są standardy, może być bardziej odpowiednie XSLT.  
  
 XSLT jest XML i w związku z tym można programowo manipulować.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ do XML programu vs. PROGRAM MSXML  
 Program MSXML jest technologią oparte na modelu COM dla przetwarzania kodu XML, która jest zawarta w systemie Microsoft Windows. Program MSXML zapewnia implementacji native modelu DOM z obsługą języka XPath i XSLT. Zawiera ona także SAX2 analizator-buforowania, oparty na zdarzeniach.  
  
 MSXML wykonuje również jest domyślnie w większości przypadków bezpieczne i dostępne w programie Internet Explorer do wykonania XML po stronie klienta przetwarzanie w aplikacje w stylu AJAX. MSXML można wykorzystać od języka programowania, obsługujący COM, C++, JavaScript, w tym i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0.  
  
 Program MSXML nie jest zalecane używanie w kodzie zarządzanym, w oparciu o środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ do XML programu vs. XmlLite  
 XmlLite jest bez buforowania, do przodu, ściągnięcia analizatora. Deweloperzy przede wszystkim za pomocą XmlLite C++. Nie zaleca się deweloperom XmlLite za pomocą kodu zarządzanego.  
  
 Główną zaletą XmlLite jest niewielka, szybkie analizator składni XML jest zabezpieczone w większości scenariuszy. Jej powierzchni zagrożenie jest bardzo mała. Jeśli chcesz chronić przed atakami, jak "odmowa usługi" lub ujawnieniem danych należy przeanalizować niezaufanych dokumentów, XmlLite może być dobrym rozwiązaniem.  
  
 XmlLite nie jest zintegrowany z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Nie przekazuje on programistę udoskonalenia wydajności, które są motywujące życie za [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
