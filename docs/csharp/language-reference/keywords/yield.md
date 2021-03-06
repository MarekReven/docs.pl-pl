---
title: "yield (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords: yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4735ab33faea71b792cbc6b567884b64bd6ca029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)
Jeśli używasz `yield` — słowo kluczowe w instrukcji, możesz wskazują, że metoda, operator lub `get` dostępu, w których występuje jest iteratora. Przy użyciu `yield` do definiowania iteratora eliminuje to potrzebę jawnego dodatkowe klasy (klasy, która przechowuje stan wyliczania, zobacz <xref:System.Collections.Generic.IEnumerator%601> przykład) podczas implementacji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> wzorzec do kolekcji niestandardowej Typ.  
  
 W poniższym przykładzie przedstawiono dwie formy `yield` instrukcji.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `yield return` instrukcji, aby zwracany był każdy element jednym naraz.  
  
 Korzystać z metodę iteratora za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub zapytania LINQ. Każdej iteracji `foreach` pętli wywołuje metodę iteratora. Gdy `yield return` osiągnięciu instrukcji w metodzie iteracyjnej `expression` jest zwracany, i są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Można użyć `yield break` instrukcji, aby zakończyć iterację.  
  
 Aby uzyskać więcej informacji na temat Iteratory, zobacz [Iteratory](../../iterators.md).  
  
## <a name="iterator-methods-and-get-accessors"></a>Metody iteratorów i pobranie akcesora  
 Deklaracja iteratora musi spełniać następujące wymagania:  
  
-   Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Deklaracja nie mogą zawierać [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametrów.  
  
 `yield` Typu zwracającą iterator <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.  Jeśli zwróci iteratora <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi być niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego.  
  
 Nie można uwzględnić `yield return` lub `yield break` instrukcji metod, które mają następujące cechy:  
  
-   Metody anonimowe. Aby uzyskać więcej informacji, zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, zobacz [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 A `yield return` instrukcja nie może znajdować się w bloku try-catch. A `yield return` instrukcja może znajdować się w bloku try instrukcji try-finally.  
  
 A `yield break` instrukcja może znajdować się w bloku try lub bloku catch, ale nie bloku finally.  
  
 Jeśli `foreach` treści (poza metodą iteratora) zgłasza wyjątek, `finally` wykonaniu bloku w metodzie iteracyjnej.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca `IEnumerable<string>` z metody iteracyjne, a następnie iteruje po jej elementów.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 Wywołanie `MyIteratorMethod` treść metody nie jest wykonywana. Zamiast tego wywołanie zwraca `IEnumerable<string>` do `elements` zmiennej.  
  
 Na iterację `foreach` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`. To wywołanie wykonuje treści `MyIteratorMethod` aż do następnego `yield return` osiągnięciu instrukcji. Wyrażenie zwracane przez `yield return` instrukcji określa nie tylko wartość `element` zmienna do użycia przez pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwość `elements`, która jest `IEnumerable<string>`.  
  
 W każdej iteracji kolejnych `foreach` pętli, wykonanie treści iteratora kontynuuje działanie od miejsca przerwał, ponownie zatrzymywanie po osiągnięciu `yield return` instrukcji. `foreach` Pętli działanie jest kończone po na końcu metody iterator lub `yield break` osiągnięciu instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `yield return` instrukcji, która znajduje się wewnątrz `for` pętli. Każdej iteracji `foreach` treść instrukcji w `Process` tworzy wywołanie `Power` funkcji iteracyjnej. Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `yield return` instrukcja, która występuje w ciągu następnej iteracji `for` pętli.  
  
 Zwracany typ metody iteracyjnej jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `get` dostępu, który jest iteratora. W tym przykładzie każdy `yield return` instrukcja zwraca wystąpienia klasy zdefiniowanej przez użytkownika.  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Instrukcja foreach w](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Iteratory](../../iterators.md)
