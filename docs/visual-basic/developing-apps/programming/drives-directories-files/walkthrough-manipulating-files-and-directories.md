---
title: Manipulowanie plikami i katalogami w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd1e61503394741e7943d30d383f2e7c5ea35f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="f17a5-102">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f17a5-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="f17a5-103">Ten przewodnik zawiera wprowadzenie do podstawowych operacji We/Wy pliku w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f17a5-103">This walkthrough provides an introduction to the fundamentals of file I/O in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="f17a5-104">Przedstawiono sposób tworzenie małych aplikacji, która zawiera listę i sprawdza, czy pliki tekstowe w katalogu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="f17a5-105">Dla każdego pliku zaznaczonego tekstu aplikacja udostępnia Atrybuty pliku i pierwszego wiersza zawartości.</span><span class="sxs-lookup"><span data-stu-id="f17a5-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="f17a5-106">Ma opcji, aby zapisać informacje o pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="f17a5-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="f17a5-107">W tym przewodniku zastosowano członkami `My.Computer.FileSystem Object`, które są dostępne w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f17a5-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="f17a5-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="f17a5-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="f17a5-109">Na końcu tego przewodnika, odpowiednik przykład została podana używającą klas z <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f17a5-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="f17a5-110">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="f17a5-110">To create the project</span></span>  
  
1.  <span data-ttu-id="f17a5-111">Na **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="f17a5-112">**Nowy projekt** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f17a5-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f17a5-113">W **zainstalowane szablony** okienku rozwiń **Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="f17a5-114">W **szablony** w środkowej, kliknij w okienku **aplikacji Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="f17a5-115">W **nazwa** wpisz `FileExplorer` Ustaw nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="f17a5-116">dodaje projekt do **Eksploratora rozwiązań**, i otwiera Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f17a5-116"> adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="f17a5-117">Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="f17a5-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="f17a5-118">Formant</span><span class="sxs-lookup"><span data-stu-id="f17a5-118">Control</span></span>|<span data-ttu-id="f17a5-119">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f17a5-119">Property</span></span>|<span data-ttu-id="f17a5-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="f17a5-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="f17a5-121">**Pola listy**</span><span class="sxs-lookup"><span data-stu-id="f17a5-121">**ListBox**</span></span>|<span data-ttu-id="f17a5-122">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f17a5-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="f17a5-123">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="f17a5-123">**Button**</span></span>|<span data-ttu-id="f17a5-124">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f17a5-124">**Name**</span></span><br /><br /> <span data-ttu-id="f17a5-125">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f17a5-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="f17a5-126">**Przeglądaj**</span><span class="sxs-lookup"><span data-stu-id="f17a5-126">**Browse**</span></span>|  
    |<span data-ttu-id="f17a5-127">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="f17a5-127">**Button**</span></span>|<span data-ttu-id="f17a5-128">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f17a5-128">**Name**</span></span><br /><br /> <span data-ttu-id="f17a5-129">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f17a5-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="f17a5-130">**Sprawdź**</span><span class="sxs-lookup"><span data-stu-id="f17a5-130">**Examine**</span></span>|  
    |<span data-ttu-id="f17a5-131">**Pole wyboru**</span><span class="sxs-lookup"><span data-stu-id="f17a5-131">**CheckBox**</span></span>|<span data-ttu-id="f17a5-132">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f17a5-132">**Name**</span></span><br /><br /> <span data-ttu-id="f17a5-133">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f17a5-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="f17a5-134">**Zapisz wyniki**</span><span class="sxs-lookup"><span data-stu-id="f17a5-134">**Save Results**</span></span>|  
    |<span data-ttu-id="f17a5-135">**FolderBrowserDialog —**</span><span class="sxs-lookup"><span data-stu-id="f17a5-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="f17a5-136">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f17a5-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="f17a5-137">Wybierz folder, oraz wyświetlanie listy plików w folderze</span><span class="sxs-lookup"><span data-stu-id="f17a5-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="f17a5-138">Utwórz `Click` programu obsługi zdarzeń dla `browseButton` przez dwukrotne kliknięcie formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="f17a5-139">Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="f17a5-140">Dodaj następujący kod do `Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     <span data-ttu-id="f17a5-141">`FolderBrowserDialog1.ShowDialog` Wywołać otwiera **przeglądanie w poszukiwaniu folderu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f17a5-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="f17a5-142">Gdy użytkownik kliknie **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwości są wysyłane jako argument `ListFiles` — metoda, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="f17a5-143">Dodaj następujące `ListFiles` metody.</span><span class="sxs-lookup"><span data-stu-id="f17a5-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     <span data-ttu-id="f17a5-144">Ten kod najpierw wyczyści **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="f17a5-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pobiera następnie kolekcji ciągów, po jednej dla każdego pliku w katalogu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="f17a5-146">`GetFiles` Metoda przyjmuje argument wzorzec wyszukiwania, pobierania plików, które jest zgodny z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="f17a5-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="f17a5-147">W tym przykładzie zwracane są tylko pliki mające rozszerzenie .txt.</span><span class="sxs-lookup"><span data-stu-id="f17a5-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="f17a5-148">Ciągi, które są zwracane przez `GetFiles` metody jest następnie dodawana do **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="f17a5-149">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f17a5-149">Run the application.</span></span> <span data-ttu-id="f17a5-150">Kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-150">Click the **Browse** button.</span></span> <span data-ttu-id="f17a5-151">W **przeglądanie w poszukiwaniu folderu** okno dialogowe, przejdź do folderu, który zawiera pliki txt, a następnie wybierz folder i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="f17a5-152">`ListBox` Zawiera listę plików txt w wybranym folderze.</span><span class="sxs-lookup"><span data-stu-id="f17a5-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="f17a5-153">Przestaną działać aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f17a5-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="f17a5-154">Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="f17a5-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="f17a5-155">Utwórz `Click` programu obsługi zdarzeń dla `examineButton` przez dwukrotne kliknięcie formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="f17a5-156">Dodaj następujący kod do `Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     <span data-ttu-id="f17a5-157">Kod sprawdza, czy element jest wybrany w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="f17a5-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="f17a5-158">Następnie uzyskuje wpis ścieżkę pliku z `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="f17a5-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="f17a5-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda służy do sprawdzenia, czy plik nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="f17a5-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="f17a5-160">Ścieżka pliku jest wysyłany jako argument `GetTextForOutput` — metoda, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="f17a5-161">Ta metoda zwraca ciąg, który zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="f17a5-162">Informacje o pliku, który jest wyświetlany w **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="f17a5-163">Dodaj następujące `GetTextForOutput` metody.</span><span class="sxs-lookup"><span data-stu-id="f17a5-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     <span data-ttu-id="f17a5-164">W kodzie użyto <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metody do uzyskania pliku parametrów.</span><span class="sxs-lookup"><span data-stu-id="f17a5-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="f17a5-165">Parametry pliku są dodawane do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="f17a5-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="f17a5-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda odczytuje zawartość pliku do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="f17a5-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="f17a5-167">Pierwszy wiersz zawartości są uzyskiwane z `StreamReader` oraz dodawane do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="f17a5-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="f17a5-168">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f17a5-168">Run the application.</span></span> <span data-ttu-id="f17a5-169">Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu zawierającego pliki txt.</span><span class="sxs-lookup"><span data-stu-id="f17a5-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="f17a5-170">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="f17a5-171">Wybierz plik w `ListBox`, a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="f17a5-172">A `MessageBox` zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="f17a5-173">Przestaną działać aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f17a5-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="f17a5-174">Aby dodać wpis dziennika</span><span class="sxs-lookup"><span data-stu-id="f17a5-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="f17a5-175">Dodaj następujący kod na końcu `examineButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     <span data-ttu-id="f17a5-176">Kod ustawia ścieżkę do pliku można umieścić w pliku dziennika w tym samym katalogu co wybranego pliku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="f17a5-177">Tekst wpisu dziennika jest ustawiona na bieżącą datę i godzinę następuje informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="f17a5-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody z `append` argument wartość `True`, jest używany do utworzenia wpisu dziennika.</span><span class="sxs-lookup"><span data-stu-id="f17a5-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="f17a5-179">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f17a5-179">Run the application.</span></span> <span data-ttu-id="f17a5-180">Przejdź do pliku tekstowego, wybierz ją w `ListBox`, wybierz pozycję **Zapisz wyniki** pole wyboru, a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="f17a5-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="f17a5-181">Sprawdź, czy wpis dziennika są zapisywane `log.txt` pliku.</span><span class="sxs-lookup"><span data-stu-id="f17a5-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="f17a5-182">Przestaną działać aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f17a5-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="f17a5-183">Aby użyć bieżącego katalogu</span><span class="sxs-lookup"><span data-stu-id="f17a5-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="f17a5-184">Tworzenie procedury obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.</span><span class="sxs-lookup"><span data-stu-id="f17a5-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="f17a5-185">Dodaj następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     <span data-ttu-id="f17a5-186">Ten kod ustawia domyślny katalog przeglądarki folderu do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="f17a5-187">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f17a5-187">Run the application.</span></span> <span data-ttu-id="f17a5-188">Po kliknięciu **Przeglądaj** po raz pierwszy, **przeglądanie w poszukiwaniu folderu** zostanie otwarte okno dialogowe do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="f17a5-189">Przestaną działać aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f17a5-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="f17a5-190">Aby włączyć formantów</span><span class="sxs-lookup"><span data-stu-id="f17a5-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="f17a5-191">Dodaj następujące `SetEnabled` metody.</span><span class="sxs-lookup"><span data-stu-id="f17a5-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     <span data-ttu-id="f17a5-192">`SetEnabled` Metoda włącza lub wyłącza formantów w zależności od tego, czy element jest wybrany w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="f17a5-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="f17a5-193">Utwórz `SelectedIndexChanged` programu obsługi zdarzeń dla `filesListBox` przez dwukrotne kliknięcie `ListBox` formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="f17a5-194">Dodaj wywołanie do `SetEnabled` w nowym `filesListBox_SelectedIndexChanged` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="f17a5-195">Dodaj wywołanie do `SetEnabled` na końcu `browseButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="f17a5-196">Dodaj wywołanie do `SetEnabled` na końcu `Form1_Load` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f17a5-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="f17a5-197">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f17a5-197">Run the application.</span></span> <span data-ttu-id="f17a5-198">**Zapisz wyniki** pole wyboru i **Sprawdź** przycisk są wyłączone, jeśli nie wybrano elementu `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="f17a5-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="f17a5-199">Pełny przykład za pomocą My.Computer.FileSystem —</span><span class="sxs-lookup"><span data-stu-id="f17a5-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="f17a5-200">Poniżej znajduje się pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="f17a5-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="f17a5-201">Pełny przykład wykorzystania System.IO</span><span class="sxs-lookup"><span data-stu-id="f17a5-201">Full example using System.IO</span></span>  
 <span data-ttu-id="f17a5-202">W poniższym przykładzie równoważne użyto klas z <xref:System.IO> przestrzeni nazw zamiast `My.Computer.FileSystem` obiektów.</span><span class="sxs-lookup"><span data-stu-id="f17a5-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f17a5-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f17a5-203">See Also</span></span>  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [<span data-ttu-id="f17a5-204">Wskazówki: Manipulowanie plikami za pomocą metod .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f17a5-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)