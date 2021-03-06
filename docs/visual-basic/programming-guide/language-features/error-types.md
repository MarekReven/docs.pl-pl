---
title: "Error — Typy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e01ed588d284a475a537a5fcf5ca506d25ca69f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="error-types-visual-basic"></a>Error — Typy (Visual Basic)
W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], błędy (nazywane również *wyjątki*) dzielą się na trzy kategorie: błędy składni, błędy środowiska wykonawczego i błędy logiczne.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 *Błędy składniowe* są wyświetlane podczas pisania kodu. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]sprawdza kod w trakcie pisania **edytora kodu** okna i powiadamia w przypadku popełnienia błędu, takie jak błędy wyraz lub nieprawidłowo przy użyciu elementu języka. Błędy składniowe są najczęściej spotykane błędy. Możesz rozwiązać je łatwo w środowisku programowania natychmiast po ich występowania.  
  
> [!NOTE]
>  `Option Explicit` Instrukcja jest jednym ze sposobów unikanie błędy składniowe. Wymusza zadeklarować z wyprzedzeniem wszystkie zmienne, które mają być używane w aplikacji. Dlatego w przypadku używania tych zmiennych w kodzie błędy związane z typografią są przechwytywane natychmiast i można naprawić.  
  
## <a name="run-time-errors"></a>Błędy środowiska wykonawczego  
 *Błędy środowiska wykonawczego* to takie, które są wyświetlane tylko po skompilować i uruchomić kod. Obejmują one kod, który może wydają się być poprawne, w tym zawiera ma błędów składni, ale nie zostanie wykonany. Na przykład może poprawnie zapisać wiersza kodu w celu otwarcia pliku. Ale jeśli plik jest uszkodzony, nie można wykonać aplikacji `Open` funkcji i jej przestanie działać. Większość błędów czasu wykonywania można rozwiązać przez ponowne zapisywanie nieprawidłowy kod, a następnie ponowną kompilację i uruchomienie go.  
  
## <a name="logic-errors"></a>Błędy logiczne  
 *Błędy logiczne* są wyświetlane, gdy aplikacja jest w użyciu. Są one większość często niepożądanych lub nieoczekiwane wyniki w odpowiedzi na działania użytkownika. Na przykład podczas przepisywania klucz lub innych poza wpływ może spowodować aplikacja przestanie działać w ramach oczekiwanych parametrów lub zupełnie. Błędy logiczne są zwykle najtrudniejsze typu, aby rozwiązać problem, ponieważ nie jest zawsze jasne, których pochodzą.  
  
## <a name="see-also"></a>Zobacz też  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)
