---
title: '&lt;participants&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 881ee8486d7939e743613fb8a0261a4fcfe7499f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltparticipantsgt-of-wcf"></a>&lt;participants&gt; w WCF
Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane. Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.  
  
 Aby uzyskać więcej informacji śledzenia przepływu pracy i uczestników śledzenia, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [uczestników śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
 \<system.serviceModel >  
\<Śledzenie >  
\<Uczestnicy >  
  
## <a name="syntax"></a>Składnia  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|Zawiera ustawienia dla uczestnika śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Śledzenie >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.|  
  
## <a name="remarks"></a>Uwagi  
 Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki. Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.  
  
 Wielu uczestników śledzenia można jednocześnie używać zdarzeń śledzenia. Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.  
  
 Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows skonfigurowany w pliku Web.config.  
  
 Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji. Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia. To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu. Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie. Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Uczestnicy śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
