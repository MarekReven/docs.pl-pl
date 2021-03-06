---
title: "Namespace ma to wpływu na jednostki odwołanie do rozszerzenia dla nowych węzłów zawierających elementy i atrybuty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b59f85eb0ef6646345eaef2a409f622c6fe4651
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace ma to wpływu na jednostki odwołanie do rozszerzenia dla nowych węzłów zawierających elementy i atrybuty
Treść jednostki deklaracji może zawierać prawie wszystko, istnieje możliwość, że zawartość może zawierać elementu jak `<!ENTITY aname "<elem>test</elem>">`.  
  
 Podczas analizowania pliku XML `&aname;` z zawartością zamiany nie jest rozwinięty w czasie analizy. Rozszerzenie pliku XML nie jest wykonywana, ponieważ rozpoznawania nazw dla elementu nie może wystąpić, dopóki węzeł znajduje się w dokumencie. Do tego czasu nie jest nie wie, jakiego przestrzeni nazw, który znajduje się w zakresie. Gdy węzeł jest włączony do dokumentu, rozpoznawane przestrzeni nazw, a wynikowy jednostki zawartości jest analizowana w jego odpowiednich węzłów.  
  
> [!NOTE]
>  W momencie rozszerzenia w węźle odwołania nowo utworzonej jednostki go nigdy nie wystąpi ponownie. W związku z tym w czasie węzła nadrzędnego jest ustawiona, są powiązane obszarów nazw używanych w tekst zastępczy dla elementu. Jednak można zmienić przestrzeni nazw dla istniejących węzłów odwołanie do jednostki po usunięciu i wstawić je w innej lokalizacji lub na węzłach odwołanie do jednostki, które są klonowane z **CloneNode** metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
