---
title: "ICorDebugILFrame::GetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP — Metoda
Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, opisujące, jak uzyskano wartość wskaźnika instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Wartość wskaźnika instrukcji.  
  
 `pMappingResult`  
 [out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugMappingResult, które opisują sposób uzyskano wartość wskaźnika instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Wartość wskaźnika instrukcji jest przesunięcie ramki stosu do kodu języka pośredniego (MSIL) firmy Microsoft przez funkcję. Jeśli ramka stosu jest aktywny, ten adres jest następną instrukcję do wykonania. Jeśli ramka stosu nie jest aktywne, ten adres jest następną instrukcję do wykonania po ponownym uaktywnieniu ramki stosu.  
  
 Jeśli ta ramka jest ramki skompilowanych just in time (JIT), wartość wskaźnika instrukcji będzie określana przez mapowanie wstecz ze wskaźnika rzeczywiste instrukcji macierzystego, co wartość może być tylko przybliżonej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
