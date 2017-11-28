---
title: "Semantyka wartości null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3820b1282dda4155946ff22784e5ebe18525b45c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="null-semantics"></a>Semantyka wartości null
Poniższa tabela zawiera linki do różnych części [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji gdzie `null` (`Nothing` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) opisano problemy.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Niezgodność typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|Sekcja "Wartości Null semantyki" tego tematu zawiera omówienie trójstanowy SQL Boolean lub dwustanowy środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Boolean>, literał `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) i `null` (C#) i inne podobne zagadnienia.|  
|[Translacja Operator zapytania standardowe](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|W sekcji "Semantyki Null" w tym temacie opisano semantykę porównania wartości null w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[Metody typu System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|W sekcji "Różnice z .NET" w tym temacie opisano, jak typ zwracany 0 z <xref:System.String.LastIndexOf%2A> może oznaczać, że ciąg ma wartość null albo czy znaleziono pozycji jest 0.|  
|[Oblicza sumę wartości liczbowych sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Opisuje sposób <xref:System.Linq.Enumerable.Sum%2A> operatora daje w wyniku `null` (`Nothing` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) zamiast 0 dla sekwencji, który zawiera tylko wartości null lub pustej sekwencji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)