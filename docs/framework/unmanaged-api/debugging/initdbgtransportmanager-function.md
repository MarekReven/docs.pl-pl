---
title: "InitDbgTransportManager — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: InitDbgTransportManager
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b849ed482f76692a63c70cbb0a3b9e1bacc8ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager — Funkcja
Inicjuje menedżera transportu do nawiązania połączenia zdalnego celu wyliczenie procesu i środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Powodzenie.  
  
 E_OUTOFMEMORY  
 Funkcja nie może przydzielić pamięci dla menedżera transportu.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Inne błędy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
