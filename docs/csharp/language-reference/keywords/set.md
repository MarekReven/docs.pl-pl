---
title: "set (odwołanie w C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords: set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a>set (odwołanie w C#)
`set` Definiuje — słowo kluczowe *akcesor* metody we właściwości lub indeksatora, która przypisuje wartość do właściwości lub indeksatora elementu. Aby uzyskać dodatkowe informacje i przykłady, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../../csharp/programming-guide/indexers/index.md).  
  
W poniższym przykładzie zdefiniowano zarówno `get` i `set` dostępu dla właściwości o nazwie `Seconds`. Używa prywatnego pole o nazwie `_seconds` kopii wartości właściwości.  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

Często `set` dostępu składa się z jednej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie. Począwszy od C# 7, można zaimplementować `set` akcesor jako element członkowski zabudowanych wyrażenia. Poniższy przykład implementuje zarówno `get` i `set` metody dostępu jako członków zabudowanych wyrażenia.

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
Proste przypadki, w którym właściwość `get` i `set` metod dostępu do wykonywania żadnych innych operacji niż ustawienie lub odczytywania wartości pola zapasowy prywatnej, można skorzystać z obsługi kompilatora C# dla właściwości zaimplementowane automatycznie. Poniższy przykład implementuje `Hours` jako właściwości zaimplementowane automatycznie. 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
