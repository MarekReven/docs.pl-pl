---
title: 'Porady: przekazywanie procedur do innej procedury w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Porady: przekazywanie procedur do innej procedury w Visual Basic
Ten przykład przedstawia sposób użycia delegatów do przekazania procedurę do innej procedury.  
  
 Delegat jest typem, który można użyć innych typów w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. `AddressOf` Operator zwraca obiektu delegowanego, po zastosowaniu na nazwę procedury.  
  
 W tym przykładzie ma procedury z parametru delegata, który może zająć odwołanie do innej procedury uzyskany z `AddressOf` operatora.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Utwórz delegata i procedur dopasowania  
  
1.  Utworzenia delegata o nazwie `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Tworzenie procedury o nazwie `AddNumbers` parametrów i wartości zwracanej, które pasują do właściwości `MathOperator`, dzięki czemu podpisy są zgodne.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Tworzenie procedury o nazwie `SubtractNumbers` za pomocą podpisu, który odpowiada `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Tworzenie procedury o nazwie `DelegateTest` pobierającej delegata jako parametr.  
  
     Ta procedura może akceptować odwołanie do `AddNumbers` lub `SubtractNumbers`, ponieważ ich podpisy są zgodne `MathOperator` podpisu.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Tworzenie procedury o nazwie `Test` wywołującym `DelegateTest` drugi raz z delegowanie dla `AddNumbers` jako parametru i ponownie z obiektem delegowanym dla `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działające na `5` i `3`, czyli 8. Następnie wynik `SubtractNumbers` na `9` i `3` jest wyświetlany, który jest 6.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty delegowane](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [AddressOf — Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegate — instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Porady: wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
