---
title: overlappedFreeError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e17e9d6a93b69d358e89109cf965b7b9856c325
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
`overlappedFreeError` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> metoda jest wywoływana przed nakładających się operacja została ukończona.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu lub uszkodzenie sterty zbierane pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Nachodzące struktury został zwolniony przed ukończeniem operacji. Funkcję, która używa wskaźnika może zapisać do struktury później, po został zwolniony. Który może spowodować uszkodzenie sterty, ponieważ inny obiekt teraz mogą zajmować tego regionu.  
  
 To zdarzenie MDA może nie reprezentować błędu, jeśli pokrywającej się z inną operacja nie została pomyślnie uruchomiona.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że operacji We/Wy przy użyciu nachodzące struktury zostało zakończone przed wywołaniem <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Oto przykładowe dane wyjściowe dla tego MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
