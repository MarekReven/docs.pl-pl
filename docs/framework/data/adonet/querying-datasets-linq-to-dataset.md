---
title: "Wykonywanie zapytania zestawów danych (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f1b1a70025dc81bdf99c636b65c23d373e73a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="querying-datasets-linq-to-dataset"></a>Wykonywanie zapytania zestawów danych (LINQ do DataSet)
Po <xref:System.Data.DataSet> obiekt został wypełniony danymi, można rozpocząć, badając ją. Formułowania zapytań dotyczących [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] jest podobny do sposobu używania [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] względem innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]— włączone źródeł danych. Należy jednak pamiętać, że gdy używasz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] odpytuje za pośrednictwem <xref:System.Data.DataSet> obiektu wyszukując wyliczenie <xref:System.Data.DataRow> obiektów zamiast wyliczenia typu niestandardowego. Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy w Twojej [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania. Dzięki temu można tworzyć zaawansowane, złożone kwerendy.  
  
 Tak jak w innych implementacjach [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], można utworzyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania w dwóch różnych formularzach: wyrażenie składnia zapytania i metody zapytań. Aby uzyskać więcej informacji o tych dwóch form, zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Za pomocą składni wyrażenia zapytania lub składnia zapytania oparte na metodzie do wykonania zapytania względem jednej tabel w <xref:System.Data.DataSet>, dla wielu tabel w <xref:System.Data.DataSet>, lub dla tabel w typizowanych <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania pojedynczej tabeli](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań pojedynczej tabeli.  
  
 [Zapytania w tabeli](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań między tabelami.  
  
 [Wykonywanie zapytania Typizowane zbiory danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Opisuje sposób tworzenia zapytań wpisany <xref:System.Data.DataSet> obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do DataSet przykłady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)