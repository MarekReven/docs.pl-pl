---
title: "COR_FIELD — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_FIELD
helpviewer_keywords: COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09a96a22a653688540bcc2ea3a03d86e242c10f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corfield-structure"></a>COR_FIELD — Struktura
Zawiera informacje dotyczące pola w obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`token`|`mdFieldDef` Token, który może służyć do pobrania informacji z pola.|  
|`offset`|Przesunięcie w bajtach, aby dane pola w obiekcie.|  
|`id`|A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje typu tego pola.|  
|`fieldType`|Wartość wyliczenia CorElementType, który wskazuje typ pola.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
