---
title: "Jak sortować i grupować dane przy użyciu widoku w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bfa1941e6352372712debb5a5243bdd24810aac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Jak sortować i grupować dane przy użyciu widoku w XAML
W tym przykładzie pokazano, jak utworzyć widok kolekcji danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Widoki pozwalają funkcje grupowanie, sortowanie, filtrowanie i podstawowe pojęcie w zakresie bieżącego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie statycznych zasobów o nazwie *umieszcza* jest zdefiniowany jako kolekcja *miejsce* obiektów, w których każdy *miejsce* obiektu jest obejmował nazwę miejscowości i Stan. Prefiks *src* jest zamapowany do przestrzeni nazw gdzie źródła danych *miejsca* jest zdefiniowany. Prefiks *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Poniższy przykład tworzy widok sortowane według nazwy mieście i w rozbiciu na stan zbierania danych.  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Widok można następnie źródle powiązania, jak w poniższym przykładzie:  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Dla powiązań do danych XML zdefiniowane w <xref:System.Windows.Data.XmlDataProvider> zasobów, należy poprzedzić nazwę XML znaku @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.CollectionViewSource>  
 [Pobieranie widoku domyślnego kolekcji danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
