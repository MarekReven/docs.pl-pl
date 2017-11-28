---
title: "&lt;developmentmode —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentmode —&gt; — Element
Określa, czy środowisko uruchomieniowe wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.  
  
 \<Konfiguracja >  
\<Runtime >  
\<developmentmode — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**developerInstallation**|Określa, czy środowisko uruchomieniowe wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**wartość true**|Wyszukiwanie zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.|  
|**wartość false**|Nie wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH. Jest to wartość domyślna|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Tego ustawienia należy używać tylko w czasie opracowywania. Środowisko uruchomieniowe nie sprawdza wersje zestawów o silnych nazwach w DEVPATH. Po prostu używa pierwszego zestawu znalezione.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak spowodować środowiska uruchomieniowego do wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Porady: Lokalizowanie zestawów za pomocą DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)