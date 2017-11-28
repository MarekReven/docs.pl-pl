---
title: "Implementacja wzorca formantu GridItem dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: daaffd02eaaf7fcb0e64dbcda4bd2ee155163f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, wraz z informacjami o właściwościach. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.GridItemPattern> — Wzorzec formantu jest używana do obsługi formantów podrzędnych poszczególnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Podczas implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Współrzędne siatki jest liczony od zera górna lewa komórka o współrzędne (0, 0).  
  
-   Scalone komórki będzie zgłaszać ich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich podstawowej zakotwiczenia komórki zgodnie z definicją w dostawcy automatyzacji interfejsu użytkownika. Zazwyczaj będzie najwyższego poziomu i lewej strony wierszy lub kolumn.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider>przewidują active manipulowania siatki, takie jak scalanie lub dzielenie komórek.  
  
-   Określa, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> zwykle można przekształcić (klient automatyzacji interfejsu użytkownika można przenieść do formantów sąsiadujące) za pomocą klawiatury.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Wymagane elementy IGridItemProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Właściwość|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych z nim metod ani zdarzenia.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu ma bez wyjątków skojarzone.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce formantów automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)