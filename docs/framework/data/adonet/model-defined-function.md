---
title: funkcja zdefiniowana przez model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e311d6e9c67a30636bdeaea7982057605678684
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="model-defined-function"></a><span data-ttu-id="ec91f-102">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="ec91f-102">model-defined function</span></span>
<span data-ttu-id="ec91f-103">A *funkcja zdefiniowana przez model* jest funkcją, która jest zdefiniowana w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ec91f-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="ec91f-104">Treść funkcji zdefiniowanej przez model jest wyrażony w [SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), dzięki czemu funkcję wyrażane niezależnie od zasady lub języki obsługiwane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ec91f-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="ec91f-105">Definicji dla funkcji zdefiniowanej przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="ec91f-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="ec91f-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec91f-106">A function name.</span></span> <span data-ttu-id="ec91f-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="ec91f-107">(Required)</span></span>  
  
-   <span data-ttu-id="ec91f-108">Typ zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="ec91f-108">The type of the return value.</span></span> <span data-ttu-id="ec91f-109">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ec91f-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec91f-110">Jeśli żaden typ zwracany jest określony, wartość zwracana jest nieważne.</span><span class="sxs-lookup"><span data-stu-id="ec91f-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="ec91f-111">Informacje o parametrach.</span><span class="sxs-lookup"><span data-stu-id="ec91f-111">Parameter information.</span></span> <span data-ttu-id="ec91f-112">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ec91f-112">(Optional)</span></span>  
  
-   <span data-ttu-id="ec91f-113">[SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) wyrażenie definiujące treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec91f-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="ec91f-114">Należy pamiętać, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ec91f-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="ec91f-115">To ograniczenie jest w miejscu, dzięki czemu mogą być składane funkcje zdefiniowane przez model.</span><span class="sxs-lookup"><span data-stu-id="ec91f-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec91f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec91f-116">Example</span></span>  
 <span data-ttu-id="ec91f-117">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="ec91f-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="ec91f-118">![Modelu z Data opublikowania](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="ec91f-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="ec91f-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="ec91f-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ec91f-120">Następujący plik CSDL definiuje funkcję w modelu koncepcyjnym zwracające liczbę lat od wystąpienia `Book` (na powyższym diagramie) został opublikowany.</span><span class="sxs-lookup"><span data-stu-id="ec91f-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="ec91f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec91f-121">See Also</span></span>  
 [<span data-ttu-id="ec91f-122">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ec91f-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ec91f-123">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ec91f-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="ec91f-124">Modelu Entity Data Model: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="ec91f-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)