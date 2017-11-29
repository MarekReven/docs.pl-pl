---
title: "&lt;proceduresignature1&gt; nie jest zgodne ze specyfikacją CLS, ponieważ przeciąża &lt;proceduresignature2&gt; który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9fca7f0590846f60577787aa476539a2c872a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; nie jest zgodne ze specyfikacją CLS, ponieważ przeciąża &lt;proceduresignature2&gt; który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych
Procedura lub właściwość jest oznaczona jako `<CLSCompliant(True)>` po zastępują innej procedury lub właściwości i jest jedyną różnicą między ich listy parametrów poziom zagnieżdżenia tablicy nieregularnej lub rangę tablicy.  
  
 W deklaracjach następujące deklaracje drugiego i trzeciego Generowanie tego błędu.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 Druga deklaracja zmienia pierwotny parametr jednowymiarowa `arrayParam` do tablicy tablic. Trzeci zmiany deklaracji `arrayParam` z tablicą dwuwymiarową (pozycja 2). Chociaż Visual Basic pozwala przeciążenia mogą się różnić tylko przez jeden z tych zmian, takich przeciążanie nie jest zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40035  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli potrzebujesz zgodności ze specyfikacją CLS, zdefiniuj z przeciążeń mogą się różnić od siebie na więcej sposobów niż tylko zmiany wymienione na tej stronie pomocy.  
  
-   Jeśli wymagasz, że przeciążeń różnią się jedynie przez zmiany wymienione w tej pomocy strony, Usuń <xref:System.CLSCompliantAttribute> z ich definicje lub oznaczyć je jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md)