---
title: "Jak przekształcać skalę modelu 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f650d968ca715e47269e0765d791856b681237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Jak przekształcać skalę modelu 3-D
Ten przykład przedstawia sposób skalowania 3-obiekt. Aby skalować 3-obiekt, należy użyć <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, I <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości Zmień rozmiar elementu przez współczynnik określisz. Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1.5 rozciąga się na 150 procent oryginalną szerokość obiektu. A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> wartość 0,5 zmniejsza wysokość obiektu 50 procent. Poniższy kod przy użyciu <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformacji dla <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie przesunięcia 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [Tworzenie sceny 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
