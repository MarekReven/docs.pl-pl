---
title: "Za pomocą klasy XslCompiledTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a00ae5a2f54aee3d6ac16d0870f9171fe42ca289
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-xslcompiledtransform-class"></a>Za pomocą klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesora XSLT programu Microsoft .NET Framework. Ta klasa jest używana do kompilowania arkusze stylów i wykonania przekształcenia XSLT.  
  
> [!NOTE]
>  Mimo że ogólną wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepszym rozwiązaniem niż <xref:System.Xml.Xsl.XslTransform> klasy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody <xref:System.Xml.Xsl.XslCompiledTransform> klasy może zapewnić więcej wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> metody <xref:System.Xml.Xsl.XslTransform> klasy pierwszy czasu wywoływana jest transformację. Jest to spowodowane musi zostać skompilowany plik XSLT, przed jego załadowaniem. Aby uzyskać więcej informacji, zobacz następującym wpisie w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dane wejściowe klasy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 W tym artykule opisano dostępne opcje wprowadzania XSLT.  
  
 [Opcje danych wyjściowych klasy XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 W tym artykule opisano dostępne opcje wyjściowe XSLT.  
  
 [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Omówienie korzystania z <xref:System.Xml.XmlResolver> klasę, aby rozpoznać zasobów zewnętrznych.  
  
 [Rozszerzanie arkuszy stylów XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 W tym artykule omówiono sposób XSLT rozszerzenia są obsługiwane.  
  
|||  
|-|-|  
|[Odwracalne błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Listy DACL zachowania dozwolone w sieci World Wide Web konsorcjum W3C XSLT zalecenie 1.0 i opisano sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.|  
|[Instrukcje: Przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Opisuje sposób przekształcania fragmentu węzła.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 W tym artykule omówiono sposób migracji kod z <xref:System.Xml.Xsl.XslTransform> — klasa  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
