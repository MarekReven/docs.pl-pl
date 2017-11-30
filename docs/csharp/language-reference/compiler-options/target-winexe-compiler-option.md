---
title: '-docelowych: winexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e155c64689f34c89443c7ff0a3dee38d6c190fcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinexe-c-compiler-options"></a><span data-ttu-id="753f4-102">/target:winexe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="753f4-102">/target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="753f4-103">**/Target: winexe** opcji powoduje, że kompilator do utworzenia pliku wykonywalnego (EXE), program systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="753f4-103">The **/target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="753f4-104">Syntax</span></span>  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="753f4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="753f4-105">Remarks</span></span>  
 <span data-ttu-id="753f4-106">Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="753f4-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="753f4-107">Windows program to taki, który udostępnia interfejs użytkownika z biblioteki .NET Framework lub z interfejsami API Win32.</span><span class="sxs-lookup"><span data-stu-id="753f4-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="753f4-108">Użyj [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) do tworzenia aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="753f4-108">Use [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="753f4-109">Chyba że określono inaczej [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="753f4-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="753f4-110">Jeśli określona w wierszu polecenia, wszystkie pliki, aż do następnego **/out** lub [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji są używane do tworzenia programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="753f4-110">When specified at the command line, all files until the next **/out** or [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="753f4-111">Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="753f4-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="753f4-112">[/Main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="753f4-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="753f4-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="753f4-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="753f4-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="753f4-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="753f4-115">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="753f4-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="753f4-116">Modyfikowanie **Output typu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="753f4-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="753f4-117">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="753f4-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="753f4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="753f4-118">Example</span></span>  
 <span data-ttu-id="753f4-119">Kompiluj `in.cs` do programu systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="753f4-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="753f4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="753f4-120">See Also</span></span>  
 [<span data-ttu-id="753f4-121">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="753f4-121">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="753f4-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="753f4-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)