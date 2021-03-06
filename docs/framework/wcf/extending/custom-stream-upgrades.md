---
title: Niestandardowe uaktualnienia strumienia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73359c293f7d29c16702e826ed6caa61149935bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-stream-upgrades"></a>Niestandardowe uaktualnienia strumienia
Zorientowane na strumień transportu, np. TCP i nazwane potoki działają na stały strumień bajtów między klientem i serwerem. Ten strumień jest realizowana <xref:System.IO.Stream> obiektu. W przypadku uaktualnienia strumienia klient chce dodać opcjonalne protokołu warstwy kanału i prosi o końcu kanał komunikacji, aby to zrobić. Uaktualnienie strumienia polega na zastąpienie oryginalnej <xref:System.IO.Stream> obiektu z uaktualnionym.  
  
 Na przykład można utworzyć strumienia kompresji bezpośrednio na strumienia transportowego. W takim przypadku oryginalnego transportu <xref:System.IO.Stream> zostanie zastąpiony nazwą otacza kompresja <xref:System.IO.Stream> wokół oryginału.  
  
 Można zastosować wiele uaktualnienia strumienia, każdy zawijania mieszanego.  
  
## <a name="how-stream-upgrades-work"></a>Sposób działania uaktualnień strumienia  
 Istnieją cztery składniki z procesem uaktualnienia strumienia.  
  
1.  Uaktualnienia strumienia *inicjatora* rozpoczyna proces: w czasie wykonywania mogą inicjować żądanie na końcu połączenie uaktualnienie warstwy transportowej kanału.  
  
2.  Uaktualnienia strumienia *wykonawca* przeprowadza uaktualnienie: w czasie wykonywania odbierze żądanie uaktualnienia z innego komputera i jeśli to możliwe, akceptuje uaktualnienia.  
  
3.  Uaktualnienie *dostawcy* tworzy *inicjatora* na kliencie i *wykonawca* na serwerze.  
  
4.  Uaktualnienie strumienia *elemencie powiązania* zostanie dodany do powiązania usługi i klienta i tworzy dostawcę w czasie wykonywania.  
  
 Należy pamiętać, że w przypadku kilku uaktualnień, inicjator i wykonawca Hermetyzowanie maszyny stanu do wymuszania które przejścia uaktualnienia są prawidłowe dla każdego inicjowania.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Jak zaimplementować uaktualnienia strumienia  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]udostępnia cztery `abstract` klasy, które można zaimplementować:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Aby zaimplementować uaktualnienia strumienia niestandardowe, wykonaj następujące czynności. Ta procedura implementuje minimalnego strumienia procesu uaktualniania na komputerach klienta i serwera.  
  
1.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> metody zaczęły w strumieniu można uaktualnić, a następnie wróć uaktualnionego strumienia. Ta metoda działa synchronicznie; istnieją podobne metody zainicjować aktualizację asynchronicznie.  
  
    2.  Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metodę sprawdzania, czy są dostępne dodatkowe uaktualnienia.  
  
2.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> metody zaczęły w strumieniu można uaktualnić, a następnie wróć uaktualnionego strumienia. Ta metoda działa synchronicznie; metodami analogiczne do akceptowania uaktualnienia asynchronicznie.  
  
    2.  Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metodę, aby określić, czy żądanie uaktualnienia jest obsługiwana przez tego uaktualnienia wykonawca na tym etapie w procesie uaktualniania.  
  
3.  Utwórz klasę implementuje <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> i <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> metody do zwrócenia wystąpień wykonawca i inicjatora zdefiniowane w kroku 2 i 1.  
  
4.  Utwórz klasę, która implementuje <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Zastąpienie <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> metody na kliencie i <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> metody dla usługi.  
  
    2.  Zastąpienie <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> metody na kliencie i <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> metody dla usługi, aby dodać uaktualnienia elementu powiązania do <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Dodaj nowy element powiązania uaktualnienia strumienia do powiązania komputerów serwera i klienta.  
  
## <a name="security-upgrades"></a>Aktualizacje zabezpieczeń  
 Dodawanie uaktualnienie zabezpieczeń to specjalna wersja strumienia ogólne procesu uaktualniania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]już zawiera dwa elementy powiązania uaktualniania zabezpieczenia strumienia. Konfiguracja zabezpieczenia na poziomie transportu jest hermetyzowany przez <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> i <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> którego można konfigurować i dodane do niestandardowego powiązania. Rozszerzenia te elementy powiązania <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> klasy, która tworzy strumień klienta i serwera uaktualnienia dostawców. Te elementy powiązania mają metody tworzące strumienia specjalne zabezpieczeń klasy dostawcy uaktualnienia, które nie są `public`, więc dla tych dwóch przypadkach wszystko co należy zrobić to dodanie elementu powiązania do powiązania.  
  
 W scenariuszach zabezpieczeń nie zostały spełnione przez powyższych elementów dwa powiązania trzy związanych z zabezpieczeniami `abstract` klas są uzyskiwane z powyższych klas podstawowych inicjatora, wykonawca i dostawcy:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Proces wdrażania uaktualnienie zabezpieczeń strumienia jest taka sama jak przed, z tą różnicą, że może pochodzić z tych trzech klas. Zastąpienie dodatkowe właściwości w tych klas, aby podać informacje o zabezpieczeniach do środowiska wykonawczego.  
  
## <a name="multiple-upgrades"></a>Kilku uaktualnień  
 Do utworzenia dodatkowych żądań uaktualnienia należy powtórzyć powyżej: Utwórz dodatkowe rozszerzenia <xref:System.ServiceModel.Channels.StreamUpgradeProvider> i elementów wiązania. Dodaj elementy do powiązania. Dodatkowe elementy są przetwarzane sekwencyjnie, rozpoczynając od pierwszego elementu powiązania dodane do powiązania. W <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> i <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> każdy dostawca uaktualnienia można określić sposób warstwy się na wszystkie istniejące uaktualnienia wiązania parametrów. Należy zastąpić go uaktualnienia istniejącej powiązanie parametru z nowego parametru złożonego uaktualnienia powiązania.  
  
 Alternatywnie jednego dostawcę uaktualnienia mogą obsługiwać kilku uaktualnień. Na przykład można zaimplementować dostawcę uaktualnienia strumienia niestandardowych, który obsługuje zarówno zabezpieczeń, jak i kompresji. Wykonaj następujące czynności:  
  
1.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> do zapisywania klasy dostawcy, która tworzy wykonawca i inicjatora.  
  
2.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> upewnieniu się zastąpić <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metodę, aby zwrócić typy zawartości dla strumienia kompresji i bezpieczne strumienia w kolejności.  
  
3.  Podklasy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> rozumie, że niestandardowe typy zawartości w jego <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metody.  
  
4.  Strumień zostanie uaktualniony po każdym wywołaniu <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> i <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
