---
title: "Porady: wywoływanie procedury właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="6eef3-102">Porady: wywoływanie procedury właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6eef3-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="6eef3-103">Przechowywanie wartości we właściwości lub pobierania jej wartość jest wywoływanie procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eef3-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="6eef3-104">Dostępu do właściwości taki sam sposób, dostęp do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6eef3-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="6eef3-105">Właściwość `Set` procedury przechowuje wartość, a jego `Get` procedury pobiera wartość.</span><span class="sxs-lookup"><span data-stu-id="6eef3-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="6eef3-106">Jednak nie zostanie jawnie wywołana procedury te według nazwy.</span><span class="sxs-lookup"><span data-stu-id="6eef3-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="6eef3-107">Możesz użyć właściwości w instrukcji przypisania lub wyrażenie, tak samo, jak będzie przechowywać lub pobrać wartości zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6eef3-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6eef3-108">wykonywania wywołań do procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eef3-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="6eef3-109">Aby wywołać procedura Get właściwości</span><span class="sxs-lookup"><span data-stu-id="6eef3-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="6eef3-110">Użyj nazwy właściwości w wyrażeniu taki sam sposób, należy użyć nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6eef3-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="6eef3-111">Można użyć właściwości dowolnym można użyć zmiennej lub stałą.</span><span class="sxs-lookup"><span data-stu-id="6eef3-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="6eef3-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="6eef3-112">-or-</span></span>  
  
     <span data-ttu-id="6eef3-113">Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="6eef3-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="6eef3-114">Poniższy przykład odczytuje wartość <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> właściwości niejawnie wywoływanie jej `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="6eef3-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="6eef3-115">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="6eef3-116">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="6eef3-117">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="6eef3-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="6eef3-118">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="6eef3-119">Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienną czy stałą lub jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="6eef3-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="6eef3-120">Wywoływanie właściwości ustawione przez procedury</span><span class="sxs-lookup"><span data-stu-id="6eef3-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="6eef3-121">Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eef3-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="6eef3-122">W poniższym przykładzie ustawiono wartość <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> właściwości niejawnie wywoływania `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="6eef3-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="6eef3-123">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="6eef3-124">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="6eef3-125">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="6eef3-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="6eef3-126">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="6eef3-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="6eef3-127">Generowane po prawej stronie instrukcji przypisania wartość jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eef3-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eef3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6eef3-128">See Also</span></span>  
 [<span data-ttu-id="6eef3-129">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="6eef3-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="6eef3-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="6eef3-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6eef3-131">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6eef3-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="6eef3-132">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6eef3-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="6eef3-133">Porady: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="6eef3-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="6eef3-134">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="6eef3-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="6eef3-135">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6eef3-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="6eef3-136">Porady: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="6eef3-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="6eef3-137">Porady: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="6eef3-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="6eef3-138">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6eef3-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="6eef3-139">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6eef3-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)