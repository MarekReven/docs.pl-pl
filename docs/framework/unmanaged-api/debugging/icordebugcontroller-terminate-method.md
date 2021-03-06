---
title: "ICorDebugController::Terminate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e7647df7a67d8357e72f8f41b0b3f586675aaac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate — Metoda
Kończy proces o określony kod zakończenia.  
  
> [!NOTE]
>  Ta metoda jest otoki dla środowiska Win32 `TerminateProcess` funkcji. W związku z tym `Terminate` używa kod zakończenia w taki sam jak robi Win32 `TerminateProcess` funkcja używa jej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exitCode`  
 [in] Wartość liczbowa jest kod wyjścia. Prawidłowe wartości liczbowe są definiowane w Winbase.h.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli proces zostanie zatrzymana, gdy `Terminate` jest wywoływana, proces powinno być kontynuowane przy użyciu [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) — metoda tak, aby debuger odbiera potwierdzenie Kończenie działania za pomocą [ ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) wywołania zwrotnego.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana przez domeny aplikacji. Oznacza to, że nie jest zaimplementowana w <xref:System.AppDomain> poziom.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
