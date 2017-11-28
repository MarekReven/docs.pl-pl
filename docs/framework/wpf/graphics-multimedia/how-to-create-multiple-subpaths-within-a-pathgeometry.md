---
title: "Jak utworzyć wiele podścieżek w obrębie PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a9a233df95f69a68c5410c5836dacd5ab2c239a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Jak utworzyć wiele podścieżek w obrębie PathGeometry
W tym przykładzie przedstawiono sposób tworzenia wielu podrzędne w <xref:System.Windows.Media.PathGeometry>. Aby utworzyć wiele ścieżek podrzędnych, należy utworzyć <xref:System.Windows.Media.PathFigure> dla podrzędnej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie ścieżki podrzędne, każdy z nich trójkąt.  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Poniższy przykład przedstawia sposób tworzenia wielu ścieżek podrzędnych za pomocą <xref:System.Windows.Shapes.Path> i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu składni. Każdy `M` tworzy nowy podrzędną, dzięki czemu w przykładzie jest tworzony dwie ścieżki podrzędne, że każdy rysowania trójkąt.  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, wersja wagi jaśniejszego <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)