---
title: "Porady: wywoływanie kompilatora wiersza polecenia (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c69860ede5620272e67bde435e6e6fa08cc81bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Porady: wywoływanie kompilatora wiersza polecenia (Visual Basic)
Można wywołać kompilatora wiersza polecenia, wpisując nazwę jego pliku wykonywalnego do wiersza polecenia, znanej także jako polecenia systemu MS-DOS. Jeśli kompilacja z domyślnego wiersza polecenia systemu Windows, należy wpisać w pełni kwalifikowana ścieżka do pliku wykonywalnego. Aby zmienić to zachowanie domyślne, można użyć [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] wiersz polecenia lub zmodyfikować zmiennej środowiskowej PATH. Umożliwiają zarówno skompilować z dowolnego katalogu, wpisując nazwę kompilatora.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Aby wywołać kompilatora przy użyciu wiersza polecenia programu Visual Studio  
  
1.  Otwórz folder programu Visual Studio Tools w obrębie grupy programu Microsoft Visual Studio.  
  
2.  Można użyć [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] wiersza polecenia, aby uzyskać dostęp do kompilatora z dowolnego katalogu na komputerze, jeśli jest zainstalowany program Visual Studio.  
  
3.  Wywołanie [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] wiersza polecenia.  
  
4.  W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.  
  
     Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy Otwórz wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Aby ustawić wartość zmiennej środowiskowej PATH kompilatora wiersza polecenia systemu Windows  
  
1.  Użyj funkcji wyszukiwania systemu Windows można znaleźć Vbc.exe na lokalnym dysku twardym.  
  
     Dokładną nazwę katalogu, w którym znajduje się kompilator zależy od lokalizacji katalogu systemu Windows i wersji ".NET Framework" zainstalowany. Jeśli masz więcej niż jedną wersję ".NET Framework" zainstalowany, należy określić wersji do użycia (zwykle najnowsza wersja).  
  
2.  Z sieci **Start** Menu, kliknij prawym przyciskiem myszy **Mój komputer**, a następnie kliknij przycisk **właściwości** z menu skrótów.  
  
3.  Kliknij przycisk **zaawansowane** , a następnie kliknij pozycję **zmiennych środowiskowych**.  
  
4.  W **systemu** zmienne okienku wybierz **ścieżki** na liście i kliknij przycisk **Edytuj**.  
  
5.  W **edycji systemu** okna dialogowego zmiennej, umieść punkt wstawiania na końcu ciągu w **wartość zmiennej** i wpisz średnikiem (;) następuje nazwa katalogu pełna w kroku 1.  
  
6.  Kliknij przycisk **OK** aby potwierdzić zmiany i zamknąć okno dialogowe.  
  
     Po zmianie zmiennej środowiskowej PATH, można uruchomić [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilator w wierszu polecenia systemu Windows z dowolnego katalogu na komputerze.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Aby wywołać kompilatora przy użyciu wiersza polecenia systemu Windows  
  
1.  Z **Start** menu, kliknij polecenie **Akcesoria** folder, a następnie otwórz **wiersza polecenia systemu Windows**.  
  
2.  W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.  
  
     Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy Otwórz wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
