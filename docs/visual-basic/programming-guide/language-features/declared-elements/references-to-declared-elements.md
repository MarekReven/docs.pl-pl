---
title: "Odwołania do elementów zadeklarowanych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9b3847164b4e577a9265a746b9329218b4af928b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="9448d-102">Odwołania do elementów zadeklarowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9448d-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="9448d-103">Gdy kod odwołuje się do elementu zadeklarowane [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora jest zgodna z nazwą w odwołania do odpowiednich deklaracja o takiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9448d-103">When your code refers to a declared element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="9448d-104">Jeśli więcej niż jeden element jest zadeklarowany jako o takiej samej nazwie, można kontrolować, które z tych elementów jest wykorzystanie przez *kwalifikującego* jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="9448d-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="9448d-105">Kompilator próbuje dopasować nazwę odwołania do nazwy deklaracji z *najwęższy zakres*.</span><span class="sxs-lookup"><span data-stu-id="9448d-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="9448d-106">Oznacza to, rozpoczyna się od kodu odniesienia i działa na zewnątrz przez kolejne poziomy zawierający elementy.</span><span class="sxs-lookup"><span data-stu-id="9448d-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="9448d-107">W poniższym przykładzie przedstawiono odwołania do dwóch zmiennych o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9448d-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="9448d-108">Przykład deklaruje dwie zmienne, każdy o nazwie `totalCount`, na różnych poziomach zakresu w module `container`.</span><span class="sxs-lookup"><span data-stu-id="9448d-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="9448d-109">Podczas procedury `showCount` Wyświetla `totalCount` bez kwalifikacji, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora Usuwa odwołanie do deklaracja o zakresie najwęższym, czyli deklaracji lokalnej wewnątrz `showCount`.</span><span class="sxs-lookup"><span data-stu-id="9448d-109">When the procedure `showCount` displays `totalCount` without qualification, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="9448d-110">Gdy kwalifikuje się `totalCount` z modułem zawierającego `container`, kompilator usuwa odwołanie do deklaracji w szerszym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9448d-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="9448d-111">Kwalifikowanie nazwy elementu</span><span class="sxs-lookup"><span data-stu-id="9448d-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="9448d-112">Jeśli chcesz zastąpić ten proces wyszukiwania i określić nazwę zadeklarowany w szerszy zakres, należy najpierw *zakwalifikować* nazwy za pomocą elementu zawierającego szerszego zakresu.</span><span class="sxs-lookup"><span data-stu-id="9448d-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="9448d-113">W niektórych przypadkach może być również konieczne zakwalifikować zawierającego element.</span><span class="sxs-lookup"><span data-stu-id="9448d-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="9448d-114">Kwalifikowanie oznacza nazwę, poprzedzającym go w instrukcji źródła informacje określające, w którym zdefiniowana jest elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="9448d-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="9448d-115">Te informacje jest nazywany *ciąg kwalifikacji*.</span><span class="sxs-lookup"><span data-stu-id="9448d-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="9448d-116">Może zawierać jeden lub więcej przestrzeni nazw i modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9448d-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="9448d-117">Ciąg kwalifikacji jednoznacznie określić modułu, klasy lub struktury zawierającej element docelowy.</span><span class="sxs-lookup"><span data-stu-id="9448d-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="9448d-118">Kontener z kolei może znajdować się w innego elementu zawierającego zwykle przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="9448d-119">Konieczne może zawierać wielu elementów zawierających w ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="9448d-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="9448d-120">Dostęp do elementu zadeklarowane przy kwalifikujących się jego nazwę</span><span class="sxs-lookup"><span data-stu-id="9448d-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="9448d-121">Określ lokalizację, w którym element został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="9448d-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="9448d-122">Może to obejmować przestrzeni nazw lub nawet hierarchii przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="9448d-123">W obszarze nazw najniższego poziomu elementu muszą być zawarte w module, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9448d-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  <span data-ttu-id="9448d-124">Określ ścieżkę kwalifikacji na podstawie lokalizacji elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9448d-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="9448d-125">Rozpoczynać się od przestrzeni nazw najwyższego poziomu, przejdź do obszaru nazw najniższym poziomie, a kończyć modułu, klasy lub struktury zawierającej element docelowy.</span><span class="sxs-lookup"><span data-stu-id="9448d-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="9448d-126">Każdy element ścieżki musi zawierać element, do którego następuje.</span><span class="sxs-lookup"><span data-stu-id="9448d-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="9448d-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="9448d-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="9448d-128">Przygotuj kwalifikacji ciągu dla elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9448d-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="9448d-129">Umieść okres (`.`) po każdym elementem w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="9448d-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="9448d-130">Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="9448d-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="9448d-131">Napisz wyrażenia lub instrukcji odwołujących się do elementu docelowego w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="9448d-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="9448d-132">Poprzedź nazwę elementu docelowego z ciągiem kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="9448d-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="9448d-133">Nazwę należy natychmiast po kropce (`.`) następujący modułu, klasy lub struktury, który zawiera element.</span><span class="sxs-lookup"><span data-stu-id="9448d-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="9448d-134">Kompilator używa ciągu kwalifikacji można znaleźć Wyczyść, jednoznaczne deklaracji, do której może dopasować odwołanie do elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9448d-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="9448d-135">Należy również kwalifikują się odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jeden element programowania, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="9448d-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="9448d-136">Na przykład <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> nazw obu zawierają `Label` klasy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="9448d-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="9448d-137">Jeśli aplikacja używa zarówno lub definiuje własną `Label` klasy, należy odróżnić różnych `Label` obiektów.</span><span class="sxs-lookup"><span data-stu-id="9448d-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="9448d-138">Alias przestrzeni nazw lub importu należy uwzględnić w deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9448d-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="9448d-139">W poniższym przykładzie użyto aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="9448d-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="9448d-140">Elementy członkowskie innych elementów zawierających</span><span class="sxs-lookup"><span data-stu-id="9448d-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="9448d-141">Użycie jest udostępniana członkiem innej klasy lub struktury, należy najpierw zakwalifikować nazwę elementu członkowskiego z zmiennej lub wyrażenie, które wskazuje na wystąpienie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9448d-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="9448d-142">W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.</span><span class="sxs-lookup"><span data-stu-id="9448d-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="9448d-143">Nazwa klasy nie można użyć, aby zakwalifikować elementu członkowskiego, który nie jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="9448d-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="9448d-144">Należy najpierw utworzyć wystąpienia w zmiennej obiektu (w tym przypadku `demoClass`), a następnie odwołania przez nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9448d-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="9448d-145">Jeśli ma klasę lub strukturę `Shared` elementu członkowskiego, możesz skorzystać ten element członkowski o nazwie klasy lub struktury lub za pomocą zmiennej lub wyrażenie wskazujące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9448d-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="9448d-146">Moduł nie ma żadnych osobnych wystąpień i jej elementów członkowskich są `Shared` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9448d-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="9448d-147">Dlatego możesz skorzystać z elementem członkowskim modułu o nazwie modułu.</span><span class="sxs-lookup"><span data-stu-id="9448d-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="9448d-148">W poniższym przykładzie przedstawiono kwalifikowanego odwołania do modułu Członkowskie procedur.</span><span class="sxs-lookup"><span data-stu-id="9448d-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="9448d-149">Przykład deklaruje dwa `Sub` procedur, o nazwie `perform`, w różnych modułach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9448d-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="9448d-150">Każdej z nich można określić bez kwalifikacji własnego modułu, ale musi być kwalifikowana, jeśli przywoływany w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9448d-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="9448d-151">Ponieważ odwoływał się w końcowym `module3` nie kwalifikuje się `perform`, kompilator nie można rozpoznać tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="9448d-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="9448d-152">Odwołania do projektów</span><span class="sxs-lookup"><span data-stu-id="9448d-152">References to Projects</span></span>  
 <span data-ttu-id="9448d-153">Aby użyć [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) elementy zdefiniowane w innym projekcie, należy najpierw ustawić *odwołania* do tego projektu biblioteki zestawu lub typu.</span><span class="sxs-lookup"><span data-stu-id="9448d-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="9448d-154">Aby ustawić odwołanie, kliknij przycisk **Dodaj odwołanie** na **projektu** menu lub użyj [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9448d-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="9448d-155">Na przykład można użyć modelu obiektów XML z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9448d-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="9448d-156">Jeśli ustawisz odwołanie <xref:System.Xml> przestrzeni nazw, można zadeklarować i użyć żadnej z jej klas, takich jak <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9448d-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="9448d-157">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9448d-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="9448d-158">Importowanie elementów zawierających</span><span class="sxs-lookup"><span data-stu-id="9448d-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="9448d-159">Można użyć [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do *zaimportować* przestrzenie nazw, które zawierają moduły lub klasy, które chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="9448d-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="9448d-160">Dzięki temu można odwoływać się do elementów zdefiniowanych w zaimportowaną przestrzenią nazw bez pełni kwalifikujących się ich nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="9448d-161">Poniższy przykład ponownie zapisuje poprzedni przykład, aby zaimportować <xref:System.Xml> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="9448d-162">Ponadto `Imports` instrukcji można zdefiniować *zaimportować alias* dla każdej importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="9448d-163">Ułatwia to kodu źródłowego, krótsze i łatwiejsze do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9448d-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="9448d-164">Poniższy przykład ponownie zapisuje poprzedni przykład, aby użyć `xD` jako alias <xref:System.Xml> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="9448d-165">`Imports` Instrukcji nie udostępnić elementy z innych projektów do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9448d-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="9448d-166">Oznacza to, że nie przyjmuje ustawienie odwołanie miejsca.</span><span class="sxs-lookup"><span data-stu-id="9448d-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="9448d-167">Importowanie przestrzeni nazw, po prostu eliminuje konieczność na kwalifikować się zdefiniowanych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9448d-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="9448d-168">Można również użyć `Imports` instrukcji, aby zaimportować moduły, klas, struktur i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9448d-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="9448d-169">Następnie można członkami takich importowanych elementów bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="9448d-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="9448d-170">Jednak należy zawsze zakwalifikować udostępniana elementów członkowskich klas i struktur za pomocą zmiennej lub wyrażenie obliczane do wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9448d-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="9448d-171">Zasady nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="9448d-171">Naming Guidelines</span></span>  
 <span data-ttu-id="9448d-172">Podczas definiowania co najmniej dwa elementy programowania, które mają taką samą nazwę, *nazwa niejednoznaczności* może występować, gdy kompilator próbuje rozpoznać odwołania do tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9448d-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="9448d-173">Jeśli więcej niż jedną definicję znajduje się w zakresie lub jeśli definicja nie znajduje się w zakresie, odwołanie jest nierozwiązywalne.</span><span class="sxs-lookup"><span data-stu-id="9448d-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="9448d-174">Na przykład zobacz "Przykład odwołania do kwalifikowanego" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="9448d-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="9448d-175">Można uniknąć niejednoznaczności, zapewniając wszystkich elementów unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="9448d-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="9448d-176">Następnie możesz wprowadzić odwołanie do każdego elementu bez konieczności jego nazwy z przestrzeni nazw, modułu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="9448d-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="9448d-177">Można także zmniejszyć ryzyko przypadkowego odwołujące się do niewłaściwego elementu.</span><span class="sxs-lookup"><span data-stu-id="9448d-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="9448d-178">Przesłanianie</span><span class="sxs-lookup"><span data-stu-id="9448d-178">Shadowing</span></span>  
 <span data-ttu-id="9448d-179">Gdy dwa elementy programowania o tej samej nazwie, jeden z nich można ukryć, lub *tle*, jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="9448d-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="9448d-180">Zasłonięty element jest niedostępny dla odwołania; Zamiast tego po kodzie używa nazwy elementu zasłonięty [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora rozpoznaje ją do elementu przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="9448d-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="9448d-181">Aby uzyskać bardziej szczegółowy opis wraz z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="9448d-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9448d-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9448d-182">See Also</span></span>  
 [<span data-ttu-id="9448d-183">Zadeklarowane nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="9448d-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="9448d-184">Zadeklarowana Charakterystyka elementów</span><span class="sxs-lookup"><span data-stu-id="9448d-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="9448d-185">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="9448d-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="9448d-186">Zmienne</span><span class="sxs-lookup"><span data-stu-id="9448d-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="9448d-187">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="9448d-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="9448d-188">New — Operator</span><span class="sxs-lookup"><span data-stu-id="9448d-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="9448d-189">Publiczna</span><span class="sxs-lookup"><span data-stu-id="9448d-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)