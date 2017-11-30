---
title: "Porady: przekazywanie argumentów do procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3debb4fa6e7b15f9c321ef207d0cc04181a98da2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="9783f-102">Porady: przekazywanie argumentów do procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9783f-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="9783f-103">Po wywołaniu procedury, możesz po nazwie procedury z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="9783f-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="9783f-104">Poddaj argument odpowiadający każdego wymaganego parametru definiuje procedurę i opcjonalnie możesz podać argumenty `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="9783f-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="9783f-105">Jeśli nie podasz `Optional` parametr w wywołaniu musi zawierać przecinka, aby oznaczyć jego miejsce na liście argumentów, jeśli są dostarczanie wszystkie pozostałe argumenty.</span><span class="sxs-lookup"><span data-stu-id="9783f-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="9783f-106">Jeśli chcesz przekazać argumentu typu danych w innym niż jego odpowiadającego mu parametru, takich jak `Byte` do `String`, można ustawić sprawdzanie typu przełącznika ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) do `Off`.</span><span class="sxs-lookup"><span data-stu-id="9783f-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="9783f-107">Jeśli `Option Strict` jest `On`, należy użyć jednego rozszerzanie konwersji lub słowa kluczowe konwersji jawnej.</span><span class="sxs-lookup"><span data-stu-id="9783f-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="9783f-108">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9783f-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="9783f-109">Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="9783f-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="9783f-110">Aby przekazać co najmniej jeden z argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="9783f-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="9783f-111">W instrukcji wywoływania wykonaj nazwę procedury w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="9783f-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="9783f-112">Wewnątrz nawiasów umieść listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="9783f-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="9783f-113">Argument dla wszystkich wymaganych parametrów definiuje procedurę obejmują i argumenty należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9783f-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="9783f-114">Upewnij się, że każdy argument jest prawidłowe wyrażenie, którego wynikiem jest typ danych można przekonwertować na typ procedury definicje odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="9783f-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="9783f-115">Jeśli parametr jest zdefiniowany jako [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md), możesz dołączyć go na liście argumentów lub pominąć go.</span><span class="sxs-lookup"><span data-stu-id="9783f-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="9783f-116">Jeśli ten parametr zostanie pominięty, procedura korzysta z wartości domyślnej zdefiniowanej dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="9783f-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="9783f-117">Jeśli zostanie pominięty argument `Optional` parametru i inny parametr po występuje on na liście parametrów, możesz oznaczyć miejsca pominięty argument przez dodatkowy przecinek na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="9783f-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="9783f-118">Następujące przykładowe wywołania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.</span><span class="sxs-lookup"><span data-stu-id="9783f-118">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     <span data-ttu-id="9783f-119">Powyższy przykład dostarcza wymagane pierwszego argumentu, który jest ciągiem komunikat do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="9783f-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="9783f-120">Argument opcjonalny drugi parametr, który określa przyciski, który będzie wyświetlany w oknie komunikatu to ciąg.</span><span class="sxs-lookup"><span data-stu-id="9783f-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="9783f-121">Ponieważ wywołania podano wartości, `MsgBox` domyślną wartość `MsgBoxStyle.OKOnly`, który zawiera tylko **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9783f-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="9783f-122">Drugi przecinek w liście argumentów oznacza miejsca pominięcia drugi argument, a ostatni ciąg jest przekazywana do opcjonalny trzeci parametr funkcji `MsgBox`, która jest tekst, który ma być wyświetlany w pasku tytułu.</span><span class="sxs-lookup"><span data-stu-id="9783f-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9783f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9783f-123">See Also</span></span>  
 [<span data-ttu-id="9783f-124">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="9783f-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="9783f-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="9783f-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="9783f-126">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="9783f-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="9783f-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="9783f-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="9783f-128">Porady: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="9783f-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="9783f-129">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="9783f-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="9783f-130">Procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="9783f-130">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="9783f-131">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="9783f-131">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="9783f-132">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="9783f-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="9783f-133">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="9783f-133">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)