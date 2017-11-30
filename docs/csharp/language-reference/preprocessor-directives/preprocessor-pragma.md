---
title: "#<a name=\"pragma-c-reference\"></a>pragma (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="95f63-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="95f63-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="95f63-103">`#pragma`zapewnia kompilator specjalne instrukcje dotyczące kompilowania pliku, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="95f63-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="95f63-104">Instrukcje musi być obsługiwana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="95f63-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="95f63-105">Innymi słowy, nie można użyć `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="95f63-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="95f63-106">Kompilator Microsoft C# obsługuje dwa `#pragma` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="95f63-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="95f63-107">Ostrzeżenie #pragma</span><span class="sxs-lookup"><span data-stu-id="95f63-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="95f63-108">sumy kontrolnej #pragma</span><span class="sxs-lookup"><span data-stu-id="95f63-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="95f63-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="95f63-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95f63-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="95f63-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="95f63-111">Nazwa pragma rozpoznany.</span><span class="sxs-lookup"><span data-stu-id="95f63-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="95f63-112">Pragma określonych argumentów.</span><span class="sxs-lookup"><span data-stu-id="95f63-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f63-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95f63-113">See Also</span></span>  
 [<span data-ttu-id="95f63-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="95f63-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95f63-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="95f63-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95f63-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="95f63-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="95f63-117">Ostrzeżenie #pragma</span><span class="sxs-lookup"><span data-stu-id="95f63-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="95f63-118">sumy kontrolnej #pragma</span><span class="sxs-lookup"><span data-stu-id="95f63-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)