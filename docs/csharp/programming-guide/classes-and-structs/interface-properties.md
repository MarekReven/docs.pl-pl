---
title: "Właściwości interfejsu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1da48adf73cccb28d9cff641948db52b40b8c1bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="21e26-102">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="21e26-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="21e26-103">Właściwości mogą być deklarowane w [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="21e26-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="21e26-104">Poniżej przedstawiono przykład metody dostępu interfejsu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="21e26-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="21e26-105">Metody dostępu właściwości interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="21e26-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="21e26-106">W związku z tym celem metody dostępu jest wskazuje, czy właściwość jest do odczytu / zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="21e26-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e26-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="21e26-107">Example</span></span>  
 <span data-ttu-id="21e26-108">W tym przykładzie interfejs `IEmployee` ma właściwość odczytu i zapisu, `Name`, a właściwość tylko do odczytu, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="21e26-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="21e26-109">Klasa `Employee` implementuje `IEmployee` interfejsu i używa te dwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="21e26-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="21e26-110">Program odczytuje nazwę nowych pracowników i bieżącą liczbę pracowników i wyświetla nazwę pracowników i numer obliczona pracownika.</span><span class="sxs-lookup"><span data-stu-id="21e26-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="21e26-111">Można użyć w pełni kwalifikowana nazwa właściwość, która odwołuje się do interfejsu, w którym zadeklarowano ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="21e26-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="21e26-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="21e26-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="21e26-113">Ta metoda jest wywoływana [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="21e26-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="21e26-114">Na przykład jeśli klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i dotyczą obu interfejsów `Name` właściwość, implementacja interfejsu jawnego członka będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="21e26-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="21e26-115">Oznacza to, że następujące deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="21e26-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="21e26-116">implementuje `Name` właściwość `IEmployee` interfejsu podczas następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="21e26-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="21e26-117">implementuje `Name` właściwość `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="21e26-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="21e26-118">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="21e26-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="21e26-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21e26-119">See Also</span></span>  
 [<span data-ttu-id="21e26-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="21e26-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="21e26-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="21e26-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="21e26-122">Przy użyciu właściwości</span><span class="sxs-lookup"><span data-stu-id="21e26-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="21e26-123">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="21e26-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="21e26-124">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="21e26-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="21e26-125">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="21e26-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)