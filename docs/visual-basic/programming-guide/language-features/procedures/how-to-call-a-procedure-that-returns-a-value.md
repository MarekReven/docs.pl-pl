---
title: "Porady: wywoływanie procedury zwracającej wartość (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6d408eed67fa417f42252bb49ecea28d4458382
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="20c83-102">Porady: wywoływanie procedury zwracającej wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20c83-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="20c83-103">A `Function` procedury zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="20c83-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="20c83-104">Należy wywołać go przez dołączenie jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="20c83-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="20c83-105">Aby wywołać procedurę Function w wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="20c83-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="20c83-106">Użyj `Function` taki sam sposób, należy użyć zmiennej Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="20c83-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="20c83-107">Można użyć `Function` wywoływanie procedury, można użyć zmiennej lub stałą w wyrażeniu dowolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="20c83-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="20c83-108">Po nazwie procedury nawiasami ujmij listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="20c83-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="20c83-109">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="20c83-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="20c83-110">Jednak za pomocą nawiasów ułatwia kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="20c83-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="20c83-111">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="20c83-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="20c83-112">Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="20c83-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="20c83-113">Alternatywnie można przekazać co najmniej jeden z argumentów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="20c83-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="20c83-114">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="20c83-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="20c83-115">Wartość zwracana z procedury uczestniczy w wyrażeniu podobnie jak wartość zmiennej lub czy stała.</span><span class="sxs-lookup"><span data-stu-id="20c83-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="20c83-116">Aby wywołać procedurę Function w instrukcji przypisania</span><span class="sxs-lookup"><span data-stu-id="20c83-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="20c83-117">Użyj `Function` nazwę procedury po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="20c83-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="20c83-118">Po nazwie procedury nawiasami ujmij listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="20c83-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="20c83-119">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="20c83-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="20c83-120">Jednak za pomocą nawiasów ułatwia kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="20c83-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="20c83-121">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="20c83-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="20c83-122">Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednie parametry, chyba że przekazaniem ich według nazwy.</span><span class="sxs-lookup"><span data-stu-id="20c83-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="20c83-123">Wartość zwracana z procedury są przechowywane w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="20c83-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20c83-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="20c83-124">Example</span></span>  
 <span data-ttu-id="20c83-125">Następujące przykładowe wywołania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> można pobrać wartości zmiennej środowiskowej systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="20c83-125">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="20c83-126">Pierwsze wywołania wiersza `Environ` w wyrażeniu, a drugi wiersz wywołuje ona w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="20c83-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="20c83-127">`Environ`pobiera nazwę zmiennej jako jedynego argumentu.</span><span class="sxs-lookup"><span data-stu-id="20c83-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="20c83-128">Zwraca wartość zmiennej do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="20c83-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20c83-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20c83-129">See Also</span></span>  
 [<span data-ttu-id="20c83-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="20c83-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="20c83-131">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="20c83-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="20c83-132">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="20c83-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="20c83-133">Porady: Tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="20c83-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="20c83-134">Porady: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="20c83-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="20c83-135">Porady: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="20c83-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)