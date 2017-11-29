---
title: "Korzystanie z biblioteki klas z platformą .NET Core w Visual Studio 2017 r."
description: "Dowiedz się, jak wywołać elementów członkowskich w bibliotece klas z programu Visual Studio 2017 r."
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
dev_langs:
- csharp
- vb
ms.openlocfilehash: 180ed868116967b03c5d4058b5618927242defc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="89bff-103">Korzystanie z biblioteki klas z platformą .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="89bff-103">Consuming a class library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="89bff-104">Po utworzeniu biblioteki klas, wykonując kroki opisane w [tworzenia biblioteki klas C# z platformą .NET Core w Visual Studio 2017](./library-with-visual-studio.md) lub [tworzenia biblioteki klas języka Visual Basic z platformą .NET Core w Visual Studio 2017](vb-library-with-visual-studio.md), testowane w [testowanie biblioteki klas z platformą .NET Core w Visual Studio 2017](testing-library-with-visual-studio.md), i wbudowane wersji biblioteki, następnym krokiem jest udostępnić obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="89bff-104">Once you've created a class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="89bff-105">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="89bff-105">You can do this in two ways:</span></span>

* <span data-ttu-id="89bff-106">Jeśli biblioteki będą używane przez pojedyncze rozwiązanie (na przykład, jeśli jest on składnikiem w pojedynczej dużych aplikacji), można dołączyć ją jako projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="89bff-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="89bff-107">Jeśli biblioteki będą zazwyczaj dostępny, można rozpowszechniać go jako pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="89bff-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="89bff-108">W tym biblioteki jako projekt w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="89bff-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="89bff-109">Tak samo, jak testy jednostkowe są dołączane do tego samego rozwiązania co biblioteki klas, mogą obejmować aplikacji w ramach tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="89bff-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="89bff-110">Na przykład można użyć w aplikacji konsoli, które monituje użytkownika o podanie ciągu i raporty, czy jego pierwszy znak jest wielką biblioteki klasy:</span><span class="sxs-lookup"><span data-stu-id="89bff-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="89bff-111">C#</span><span class="sxs-lookup"><span data-stu-id="89bff-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="89bff-112">Otwórz `ClassLibraryProjects` rozwiązania utworzone w [tworzenia biblioteki klas C# z platformą .NET Core w Visual Studio 2017](./library-with-visual-studio.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="89bff-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="89bff-113">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania i wybierz **Dodaj** > **nowy projekt** z menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="89bff-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="89bff-114">W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual C#** a następnie wybierz węzeł **.NET Core** węzła następuje **aplikacji konsoli (.NET Core)** szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="89bff-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="89bff-115">W **nazwa** polu tekstowym, wpisz "Pokazy" i wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="89bff-117">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokazy** projekt i wybierz **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="89bff-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Menu kontekstowe pokazy](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="89bff-119">Początkowo projektu nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="89bff-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="89bff-120">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="89bff-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="89bff-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="89bff-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe pokazy zależności](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="89bff-123">W **Menedżera odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projektu biblioteki klas, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Menedżera odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="89bff-125">W oknie Kod *Program.cs* pliku, Zastąp cały kod z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="89bff-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="89bff-126">W kodzie użyto [Console.WindowHeight](xref:System.Console.WindowHeight) właściwości, aby określić liczbę wierszy w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-126">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="89bff-127">Zawsze, gdy [Console.CursorTop](xref:System.Console.CursorTop) właściwości jest większa lub równa liczbie wierszy w oknie konsoli, kod Czyści okno konsoli i komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="89bff-127">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="89bff-128">Program monituje użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="89bff-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="89bff-129">Wskazuje, czy ciąg rozpoczyna się wielką literę.</span><span class="sxs-lookup"><span data-stu-id="89bff-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="89bff-130">Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciąg, kończy aplikacji i zamyka okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="89bff-131">W razie potrzeby zmień narzędzi, aby skompilować **debugowania** wydanie `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="89bff-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="89bff-132">Kompilowanie i uruchamianie programu wybierając zieloną strzałkę na **pokazy** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="89bff-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89bff-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="89bff-135">Otwórz `ClassLibraryProjects` rozwiązania utworzone w [Tworzenie klasy biblioteki z Visual Basic i .NET Core w Visual Studio 2017](vb-library-with-visual-studio.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="89bff-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="89bff-136">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania i wybierz **Dodaj** > **nowy projekt** z menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="89bff-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="89bff-137">W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual Basic** a następnie wybierz węzeł **.NET Core** węzła następuje **aplikacji konsoli (.NET Core)**szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="89bff-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="89bff-138">W **nazwa** polu tekstowym, wpisz "Pokazy" i wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="89bff-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokazy** projekt i wybierz **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="89bff-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Menu kontekstowe pokazy](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="89bff-142">Początkowo projektu nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="89bff-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="89bff-143">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="89bff-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="89bff-144">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="89bff-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe pokazy zależności](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="89bff-146">W **Menedżera odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projektu biblioteki klas, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Menedżera odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="89bff-148">W oknie Kod *Program.vb* pliku, Zastąp cały kod z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="89bff-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="89bff-149">W kodzie użyto [Console.WindowHeight](xref:System.Console.WindowHeight) właściwości, aby określić liczbę wierszy w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-149">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="89bff-150">Zawsze, gdy [Console.CursorTop](xref:System.Console.CursorTop) właściwości jest większa lub równa liczbie wierszy w oknie konsoli, kod Czyści okno konsoli i komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="89bff-150">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="89bff-151">Program monituje użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="89bff-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="89bff-152">Wskazuje, czy ciąg rozpoczyna się wielką literę.</span><span class="sxs-lookup"><span data-stu-id="89bff-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="89bff-153">Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciąg, kończy aplikacji i zamyka okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="89bff-154">W razie potrzeby zmień narzędzi, aby skompilować **debugowania** wydanie `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="89bff-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="89bff-155">Kompilowanie i uruchamianie programu wybierając zieloną strzałkę na **pokazy** przycisku.</span><span class="sxs-lookup"><span data-stu-id="89bff-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="89bff-157">Można debugować i opublikować aplikację, która korzysta z tej biblioteki, wykonując kroki opisane w [debugowania aplikacji Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md) i [publikowania aplikacji Hello World z programem Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="89bff-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="89bff-158">Dystrybucja biblioteki w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="89bff-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="89bff-159">Można udostępnić biblioteki klasy powszechnie publikując go jako pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="89bff-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="89bff-160">Program Visual Studio nie obsługuje tworzenia pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="89bff-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="89bff-161">Aby utworzyć bramę, należy użyć [ `dotnet` narzędzia wiersza polecenia](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="89bff-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="89bff-162">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-162">Open a console window.</span></span> <span data-ttu-id="89bff-163">Na przykład w **Pytaj niczego** tekst pola na pasku zadań systemu Windows, wprowadź `Command Prompt` (lub `cmd` skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** aplikacji komputerowej lub naciskając klawisz Enter, jeśli jest zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="89bff-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="89bff-164">Przejdź do katalogu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="89bff-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="89bff-165">O ile nie zostało ponownie skonfigurować lokalizację pliku typowe, znajduje się on w *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* katalogu.</span><span class="sxs-lookup"><span data-stu-id="89bff-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="89bff-166">Katalog zawiera kod źródłowy i plik projektu *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="89bff-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="89bff-167">Należy wydać polecenie `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="89bff-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="89bff-168">`dotnet` Narzędzie generuje pakiet o *.nupkg* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="89bff-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="89bff-169">Jeśli katalog zawierający *dotnet.exe* jest nie znajduje się w ŚCIEŻCE, można znaleźć lokalizacji, wprowadzając `where dotnet.exe` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="89bff-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="89bff-170">Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [Tworzenie pakietu NuGet narzędziami Cross Platform](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="89bff-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>