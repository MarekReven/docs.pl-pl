---
title: '&lt;Host&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7177c62af8501258ad8709bff88cb85488b56727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lthostgt"></a>&lt;Host&gt;
Określa ustawienia dla usługi hosta.  
  
 \<System. ServiceModel >  
\<usługi >  
\<usługi >  
\<host >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekcja `baseAddress` elementów, które określa adres podstawowy używany przez hosta usługi.|  
|[\<limity czasu >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie usługi hosta.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Określa ustawienia dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
