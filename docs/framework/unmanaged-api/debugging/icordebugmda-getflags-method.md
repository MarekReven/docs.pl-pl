---
title: "ICorDebugMDA::GetFlags — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f5a44d3bf0c689c0deb0e8c59b64124173f5645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetflags-method"></a>ICorDebugMDA::GetFlags — Metoda
Pobiera flagi skojarzone z zarządzany Asystent debugowania (MDA) reprezentowany przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlags`  
 [in] Bitowe połączenie [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) wartości wyliczenia, które określają ustawienia flagi to zdarzenie MDA.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMDA, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
