---
title: "Porady: łączenie kwerend LINQ za pomocą wyrażeń regularnych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36e609944d1eaf95c0573ef4b63f2bf6c573932b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="35a99-102">Porady: łączenie kwerend LINQ za pomocą wyrażeń regularnych (C#)</span><span class="sxs-lookup"><span data-stu-id="35a99-102">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>
<span data-ttu-id="35a99-103">Ten przykład przedstawia sposób użycia <xref:System.Text.RegularExpressions.Regex> klasa do tworzenia wyrażenia regularnego do dopasowania bardziej złożone w ciągów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="35a99-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="35a99-104">Zapytania LINQ ułatwia filtr na dokładnie te pliki, które chcesz wyszukiwania z wyrażeniem regularnym i kształtu wyniki.</span><span class="sxs-lookup"><span data-stu-id="35a99-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35a99-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="35a99-105">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a   
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write   
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery   
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="35a99-106">Należy pamiętać, że możesz także zbadać <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest zwracany przez `RegEx` wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="35a99-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="35a99-107">W tym przykładzie wartość każdego dopasowanie jest generowany w wynikach.</span><span class="sxs-lookup"><span data-stu-id="35a99-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="35a99-108">Jednak istnieje również możliwość używania LINQ do wykonywania wszystkich rodzajów filtrowanie, sortowanie i grupowanie w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="35a99-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="35a99-109">Ponieważ <xref:System.Text.RegularExpressions.MatchCollection> jest inny niż ogólny <xref:System.Collections.IEnumerable> kolekcji, trzeba jawnie określać typu zmienną zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="35a99-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35a99-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35a99-110">Compiling the Code</span></span>  
 <span data-ttu-id="35a99-111">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="35a99-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a99-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35a99-112">See Also</span></span>  
 [<span data-ttu-id="35a99-113">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="35a99-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="35a99-114">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="35a99-114">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)