---
title: "IHostMAlloc::DebugAlloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.DebugAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18759aa319bf39c49418e3b9388d96829ed52f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="cc773-102">IHostMAlloc::DebugAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc773-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="cc773-103">Żąda przydzielić określoną ilością pamięci sterty hosta, a ponadto śledzić, gdzie została przydzielona pamięć.</span><span class="sxs-lookup"><span data-stu-id="cc773-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc773-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc773-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc773-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc773-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="cc773-106">[in] Rozmiar w bajtach, bieżącego żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="cc773-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="cc773-107">[in] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości i wskazujący wpływ błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="cc773-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="cc773-108">[in] Plik kodu wykonywalnego debugowany.</span><span class="sxs-lookup"><span data-stu-id="cc773-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="cc773-109">[in] Numer wiersza w `pszFileName` których alokacji zażądano.</span><span class="sxs-lookup"><span data-stu-id="cc773-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="cc773-110">[out] Wskaźnik do alokacji pamięci lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="cc773-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc773-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc773-111">Return Value</span></span>  
  
|<span data-ttu-id="cc773-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc773-112">HRESULT</span></span>|<span data-ttu-id="cc773-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cc773-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc773-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc773-114">S_OK</span></span>|<span data-ttu-id="cc773-115">`DebugAlloc`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cc773-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="cc773-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc773-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc773-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cc773-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc773-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc773-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc773-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cc773-119">The call timed out.</span></span>|  
|<span data-ttu-id="cc773-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc773-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc773-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="cc773-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc773-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc773-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc773-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cc773-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc773-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc773-124">E_FAIL</span></span>|<span data-ttu-id="cc773-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cc773-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc773-126">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cc773-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc773-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc773-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cc773-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cc773-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cc773-129">Za mało pamięci nie była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="cc773-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc773-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc773-130">Remarks</span></span>  
 <span data-ttu-id="cc773-131">Środowisko CLR pobiera wskaźnika interfejsu do [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienia przez wywołanie metody [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cc773-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="cc773-132">`DebugAlloc`Umożliwia środowiska wykonawczego uzyskać informacje o pliku kodu do użycia podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="cc773-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc773-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc773-133">Requirements</span></span>  
 <span data-ttu-id="cc773-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc773-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc773-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc773-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc773-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc773-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc773-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc773-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc773-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc773-138">See Also</span></span>  
 [<span data-ttu-id="cc773-139">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="cc773-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="cc773-140">IHostMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="cc773-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)