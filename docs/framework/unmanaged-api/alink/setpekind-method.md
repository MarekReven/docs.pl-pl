---
title: "SetPEKind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d511bcda2ab4e879c123d866b3f6c887173c1d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="setpekind-method"></a><span data-ttu-id="47a8c-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="47a8c-102">SetPEKind Method</span></span>
<span data-ttu-id="47a8c-103">Określa typ przenośnego pliku wykonywalnego, komputera lub pochodzącego od dowolnego komputera.</span><span class="sxs-lookup"><span data-stu-id="47a8c-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47a8c-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="47a8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47a8c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="47a8c-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="47a8c-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="47a8c-107">Token pliku, dla którego należy ustawić typ PE.</span><span class="sxs-lookup"><span data-stu-id="47a8c-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="47a8c-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niezwiązanego modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="47a8c-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="47a8c-109">Typ środowiska Preinstalacyjnego wskazywany przez [CorPEKind — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="47a8c-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="47a8c-110">Architektura komputera docelowego, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="47a8c-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47a8c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="47a8c-111">Return Value</span></span>  
 <span data-ttu-id="47a8c-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="47a8c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a8c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47a8c-113">Requirements</span></span>  
 <span data-ttu-id="47a8c-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="47a8c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a8c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47a8c-115">See Also</span></span>  
 [<span data-ttu-id="47a8c-116">GetPEKind — metoda</span><span class="sxs-lookup"><span data-stu-id="47a8c-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="47a8c-117">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="47a8c-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="47a8c-118">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="47a8c-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="47a8c-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="47a8c-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)