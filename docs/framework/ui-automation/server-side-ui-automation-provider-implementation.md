---
title: "Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
caps.latest.revision: "39"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d25f561444cd672e8842711025f4299c375d6bb4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tej sekcji opisano, jak do implementowania dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla kontrolek niestandardowych.  
  
 Implementację [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] elementów i z systemem innym niż-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementów (takich jak przeznaczone dla [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) różni się. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]elementy zapewniają obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez klasę pochodną <xref:System.Windows.Automation.Peers.AutomationPeer>. Z systemem innym niż[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy zapewniają obsługę przez implementacje interfejsów dostawcy.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Powinien być zapisywany dostawców, dzięki czemu mogą one działać w środowisku z częściowym zaufaniem. Ponieważ UIAutomationClient.dll nie jest skonfigurowana do uruchamiania w częściowej relacji zaufania, dostawca kod nie powinien odwoływać się tego zestawu. Jeśli jednak kod może uruchamiane w środowisku pełnego zaufania, ale następnie kończą się niepowodzeniem w środowisku z częściowym zaufaniem.  
  
 W szczególności należy używać pola z klas w UIAutomationClient.dll, takich jak te w <xref:System.Windows.Automation.AutomationElement>. Użyj pola równoważne z klas w UIAutomationTypes.dll, takich jak <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implementacja dostawcy przez Windows Presentation Foundation elementy  
 Aby uzyskać więcej informacji na ten temat, zobacz [automatyzacji interfejsu użytkownika, które Kontrolki niestandardowe WPF](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>Implementacja dostawcy przez elementy z systemem innym niż WPF  
 Kontrolki niestandardowe, które są nie jest częścią [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework, ale są zapisywane w kodzie zarządzanym (najczęściej są [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] formantów), zapewniają obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dzięki implementacji interfejsów. Każdy element musi implementować co najmniej jednego z interfejsów wymienionych w pierwszej tabeli w następnej sekcji. Ponadto jeśli element obsługuje jeden lub kilka wzorców formantu, musi implementować odpowiedni interfejs dla każdego — wzorzec formantu.  
  
 Twoje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] projektu dostawcy musi odwoływać się następujące zestawy:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Interfejsy dostawcy  
 Każdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawca musi implementować jeden z następujących interfejsów.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Zapewnia funkcje dla prostego formantu w oknie, w tym obsługa wzorców formantu i właściwości.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Dziedziczy <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Dodaje funkcjonalność dotyczącą element w kontrolce złożonych, tym nawigację w obrębie fragmentu, Ustawianie fokusu i zwracanie prostokątem elementu.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Dziedziczy <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Dodaje funkcje dla elementu głównego w złożonych formantu, w tym lokalizowania elementu podrzędnego w określonych współrzędnych i ustawiania stanu fokus dla całego formantu.|  
  
 Następujące interfejsy dodawać żadnych funkcji, ale nie są wymagane do zaimplementowania.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Umożliwia dostawcy do śledzenia żądań zdarzeń.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Umożliwia zmienianie położenia elementów na podstawie okna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa fragmentu.|  
  
 Wszystkie interfejsy w <xref:System.Windows.Automation.Provider> przestrzeni nazw są obsługi — wzorzec formantu.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>Wymagania dotyczące dostawców innych niż WPF  
 Aby komunikować się z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], formantu musi implementować następujące główne obszary funkcji:  
  
|Funkcja|Implementacja|  
|-------------------|--------------------|  
|Udostępnianie dostawcy do[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|W odpowiedzi na wiadomość WM_GETOBJECT wysyłane do okna kontrolki, zwracać obiekt, który implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (lub interfejsu pochodnego). Fragmenty musi to być dostawcy dla elementu głównego fragmentu.|  
|Podaj wartości właściwości|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> ani i Zastąp wartości.|  
|Włącz klienta do interakcji z formantem|Implementowanie interfejsów, które obsługuje wzorce formantu <xref:System.Windows.Automation.Provider.IInvokeProvider>. Zwraca tych dostawców wzorca w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Wywoływanie zdarzeń|Wywołania jednej z metod statycznych <xref:System.Windows.Automation.Provider.AutomationInteropProvider> Aby zgłosić zdarzenie, które klient może nasłuchiwać.|  
|Włączanie nawigacji i koncentrujących się w obrębie fragmentu|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> dla każdego elementu w obrębie fragmentu. (Nie niezbędne dla elementów, które nie są częścią fragment.)|  
|Włącz koncentrujących się i położenie elementu podrzędnego w fragmentu|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Nie jest konieczna dla elementów, które są fragmentu nie katalogów głównych.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Wartości właściwości wśród dostawców innych niż WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]dostawców w przypadku kontrolek niestandardowych musi obsługiwać niektórych właściwości, które mogą być używane przez system automatyzacji, jak również przez aplikacje klienckie. Dla elementów, które są obsługiwane w systemie windows (parametrów hWnd) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można pobrać niektórych właściwości pochodzących od domyślnego dostawcy okna, ale musi uzyskać inne osoby z niestandardowego dostawcy.  
  
 Dostawców dla formantów HWND na podstawie zazwyczaj nie zapewnienie następujących właściwości (określone przez wartości pól):  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Prostego elementu lub fragmentu hostowanej w oknie głównym są uzyskiwane z okna; jednak podać własne identyfikatory elementów fragmentu poniżej katalogu głównego (na przykład listę elementów w polu listy). Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Powinny być zwracane dla dostawców hostowanych w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] formantu. Domyślny dostawca okna może być w tym przypadku nie można pobrać poprawną wartość.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Zwykle jest dostarczana przez dostawcę hosta. Na przykład, jeśli formant niestandardowy jest pochodną <xref:System.Windows.Forms.Control>, nazwa pochodzi od `Text` właściwości formantu.  
  
 Na przykład kodu, zobacz [właściwości zwrot od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>Zdarzenia w dostawców innych niż WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]dostawców powinny wywoływać zdarzeń powiadomiono aplikacje klienckie zmian w stan interfejsu użytkownika. Następujące metody umożliwiają wywoływanie zdarzeń.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Uruchamia różne zdarzenia, w tym zdarzenia wyzwolone przez wzorce formantu.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Zgłasza zdarzenie, gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwość zostanie zmieniona.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Zgłasza zdarzenie, gdy struktura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa został zmieniony; na przykład przez usunięcie lub dodanie elementu.|  
  
 Zdarzenie ma na celu powiadomić klienta elementu miejsce [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], czy działanie jest wyzwalany przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sam system. Na przykład zdarzenia, które są identyfikowane przez <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> powinien być wywoływany, gdy formant jest wywoływany przez dane wejściowe użytkownika bezpośrednio lub przez wywołanie aplikacji klienta <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Aby zoptymalizować wydajność, dostawcę można selektywnie wywoływanie zdarzeń lub w ogóle Zgłoś żadne zdarzenia, jeśli żadna aplikacja klienta jest zarejestrowany do ich odbierania. Następujące metody są używane do optymalizacji.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Ta właściwość statyczna Określa, czy wszystkie aplikacje klienckie subskrybuje, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Dostawcy implementację tego interfejsu w folderze głównym fragmentu umożliwia zalecana, gdy klienci rejestrowanie i wyrejestrowywanie programy obsługi zdarzeń dla zdarzenia na fragmentu.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>Nawigacji dostawcy z systemem innym niż WPF  
 Dostawców dla prostego formanty, takie jak przycisk niestandardowy hostowanej w oknie (HWND) musi obsługiwać nawigację w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Nawigacja do i z elementu jest obsługiwane przez domyślnego dostawcę dla okno hosta, które jest określone w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Podczas implementowania dostawcy złożonych kontrolki niestandardowej, jednak musi obsługiwać nawigacji węzła głównego fragmentu i jego elementy podrzędne oraz między węzłami tego samego poziomu.  
  
> [!NOTE]
>  Elementy fragmentu innego niż root musi zwracać `null` odwołania z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, ponieważ nie są one bezpośrednio hostowana w oknie i żaden dostawca domyślne może obsługiwać nawigacji do i z nich.  
  
 Struktura fragmentu zależy od implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Dla każdego możliwe kierunku z każdego fragmentu ta metoda zwraca obiekt dostawcy dla elementu w tym kierunku. Jeśli istnieje żaden element w tym kierunku, metoda zwraca `null` odwołania.  
  
 Główny fragmentu obsługuje nawigacji tylko do elementów podrzędnych. Na przykład pole listy zwraca pierwszy element na liście po kierunek <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>oraz ostatniego elementu, gdy jest skierowany <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Główny fragmentu nie obsługuje nawigacji do elementu nadrzędnego lub elementy równorzędne; jest to obsługiwane przez dostawcę okno hosta.  
  
 Elementy fragment, które nie są w folderze głównym musi obsługiwać nawigacji do elementu nadrzędnego, a wśród elementów równorzędnych i elementy podrzędne, które mają.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>Dostawca nie WPF Reparenting  
 Wyskakujące są faktycznie najwyższego poziomu systemu windows, a więc domyślnie są wyświetlane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jako elementy podrzędne pulpitu. W wielu przypadkach jednak wyskakujące są logicznie dzieci niektóre inne kontrolki. Na przykład listy rozwijanej pola kombi logicznie jest elementem podrzędnym elementu pola kombi. Podobnie okno podręczne menu logicznie jest elementem podrzędnym elementu menu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia obsługę nadrzędne wyskakujące, aby były wyświetlane jako elementy podrzędne skojarzony formant.  
  
 Aby zmienić elementu nadrzędnego okno podręczne:  
  
1.  Utwórz dostawcę dla tego okna. Wymaga to góry znane klasy okna podręcznego.  
  
2.  Tak, jakby była formantu w osobnym implementuje wszystkich właściwości i wzorce dla tego oknie podręcznym.  
  
3.  Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> właściwości, tak aby zwraca wartość uzyskane z <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, gdzie parametr jest uchwytu okna podręcznego okna.  
  
4.  Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> wyskakujące okno i jego elementu nadrzędnego, tak że nawigacja odbywa się prawidłowo z logiczny obiekt nadrzędny do logicznych elementów podrzędnych i między elementy podrzędne tego samego poziomu.  
  
 Gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] napotka okna podręcznego rozpoznaje nawigacji jest zastępowana z domyślnego i nakłada się na okno podręczne po napotkaniu się jako element podrzędny pulpitu. Zamiast tego węzła tylko będzie dostępny za pośrednictwem fragmentu.  
  
 Reparenting nie jest odpowiednia dla przypadków, gdy formant może obsługiwać okna dowolnej klasy. Na przykład paska pomocniczego może obsługiwać dowolny typ HWND w jego pasma. Aby obsługiwać te przypadki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługuje alternatywny relokacji HWND w sposób opisany w następnej sekcji.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>Zmienianie położenia dostawcy z systemem innym niż WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fragmenty może zawierać co najmniej dwa elementy, które każdy znajdują się w oknie (HWND). Ponieważ każdy HWND ma własną domyślnego dostawcę, który uwzględnia HWND za elementem podrzędnym elementu zawierającego HWND, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa domyślnie wyświetli parametrów hWnd we fragmencie jako elementy podrzędne okno nadrzędne. W większości przypadków jest to zachowanie pożądane, ale niekiedy może to prowadzić do pomyłek, ponieważ nie odpowiada struktury logicznej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Dobrym przykładem jest formantem paska pomocniczego. Paska pomocniczego zawiera grup, które z kolei może zawierać HWND na podstawie formantu paska narzędzi, pole edycji lub pola kombi. Okno domyślnego dostawcę dla paska pomocniczego HWND widzi pasek sterowania parametrów hWnd jako elementy podrzędne, a dostawca paska pomocniczego widzi grup jako elementy podrzędne. Ponieważ dostawca HWND dostawcy paska pomocniczego działa w połączeniu i łączenie ich elementy podrzędne, zarówno grup i formantów na podstawie HWND są wyświetlane jako elementy podrzędne paska pomocniczego. Logicznie jednak tylko grup powinny się wyświetlać jako elementy podrzędne paska pomocniczego, a każdy dostawca pasmem powinny być połączone z domyślnego dostawcę HWND formantu, który zawiera.  
  
 W tym celu dla dostawcy fragmentu głównego paska pomocniczego udostępnia zestaw elementów podrzędnych reprezentujący grup. Każdy pasmem ma jednego dostawcy, który może narazić właściwości i wzorce. Jego wykonywania <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, dostawca pasmem zwraca domyślnego dostawcę okna dla formantu HWND, która uzyskuje on przez wywołanie metody <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, przekazując uchwyt okna formantu. Na koniec implementuje dostawcę fragmentu głównego dla paska pomocniczego <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> interfejsu w jej implementacja <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> zwraca dostawcy odpowiednie poza pasmem dla formantu zawartych w określonym HWND.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)  
 [Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)  
 [Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Przykład prostego dostawcy](http://msdn.microsoft.com/library/c10a6255-e8dc-494b-a051-15111b47984a)  
 [Przykładowe dostawcy fragmentu](http://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
