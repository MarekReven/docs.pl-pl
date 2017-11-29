---
title: "CorDebugInternalFrameType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInternalFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugInternalFrameType
helpviewer_keywords: CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b21e50c86a09092e7df65e5fddefb515f6838b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="36341-102">CorDebugInternalFrameType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="36341-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="36341-103">Określa typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="36341-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="36341-104">To wyliczenie jest używany przez [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="36341-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36341-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36341-105">Syntax</span></span>  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="36341-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="36341-106">Members</span></span>  
  
|<span data-ttu-id="36341-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="36341-107">Member</span></span>|<span data-ttu-id="36341-108">Opis</span><span class="sxs-lookup"><span data-stu-id="36341-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="36341-109">Wartość null.</span><span class="sxs-lookup"><span data-stu-id="36341-109">A null value.</span></span> <span data-ttu-id="36341-110">`ICorDebugInternalFrame::GetFrameType` Metody nigdy nie zwraca tę wartość.</span><span class="sxs-lookup"><span data-stu-id="36341-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="36341-111">Ramka stub niezarządzany zarządzany.</span><span class="sxs-lookup"><span data-stu-id="36341-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="36341-112">Ramka stub niezarządzanych do zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="36341-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="36341-113">Przejścia między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36341-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="36341-114">Wywołanie metody lightweight.</span><span class="sxs-lookup"><span data-stu-id="36341-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="36341-115">Początek obliczania funkcji.</span><span class="sxs-lookup"><span data-stu-id="36341-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="36341-116">Wywoływana wewnętrznie do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="36341-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="36341-117">Początek inicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="36341-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="36341-118">Wyjątek zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="36341-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="36341-119">Ramka, używany do zabezpieczenia dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="36341-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="36341-120">Środowisko wykonawcze jest metoda kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="36341-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36341-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36341-121">Requirements</span></span>  
 <span data-ttu-id="36341-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36341-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36341-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36341-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36341-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36341-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36341-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36341-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36341-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36341-126">See Also</span></span>  
 [<span data-ttu-id="36341-127">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="36341-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)