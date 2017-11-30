---
title: "ICorProfilerInfo::GetFunctionFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c7366df7d2213740f640590364b1cb4d28876115
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="d71c2-102">ICorProfilerInfo::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="d71c2-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="d71c2-103">Pobiera identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="d71c2-103">Gets the ID of a function.</span></span> <span data-ttu-id="d71c2-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="d71c2-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d71c2-105">Użyj [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d71c2-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71c2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d71c2-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d71c2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d71c2-107">Remarks</span></span>  
 <span data-ttu-id="d71c2-108">`GetFunctionFromToken` Metoda nie będzie działać dla funkcje ogólne lub funkcji w typach ogólnych; jest już nieaktualny.</span><span class="sxs-lookup"><span data-stu-id="d71c2-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="d71c2-109">Użyj `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` dla wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="d71c2-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71c2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d71c2-110">Requirements</span></span>  
 <span data-ttu-id="d71c2-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d71c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71c2-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d71c2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d71c2-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d71c2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d71c2-114">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="d71c2-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71c2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d71c2-115">See Also</span></span>  
 [<span data-ttu-id="d71c2-116">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="d71c2-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)