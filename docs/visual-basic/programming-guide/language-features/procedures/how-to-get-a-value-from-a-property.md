---
title: "Porady: pobieranie wartości z właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Porady: pobieranie wartości z właściwości (Visual Basic)
Możesz pobrać wartości właściwości, łącznie z nazwą właściwości w wyrażeniu.  
  
 Właściwość `Get` procedury pobiera wartość, ale nie zostanie jawnie wywołana go według nazwy. Użyj właściwości, tak jak w przypadku zmiennej. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wykonywania wywołań do procedury właściwości.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Aby pobrać wartości z właściwości  
  
1.  Użyj nazwy właściwości w wyrażeniu taki sam sposób, należy użyć nazwy zmiennej. Można użyć właściwości dowolnym można użyć zmiennej lub stałą.  
  
     —lub—  
  
     Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` właściwości niejawnie wywoływanie jej `Get` procedury.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
 Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienną czy stałą lub jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Porady: Tworzenie właściwości](./how-to-create-a-property.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Porady: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
