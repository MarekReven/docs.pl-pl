---
title: "Protokół PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 805f6f6ed7990b42065dfe7985a5d81844961897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="378eb-102">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="378eb-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="378eb-103">W środowiskach peer-to-peer elementów równorzędnych użyć systemy rozpoznawania nazw określonych w ustalaniu każdej lokalizacji sieciowych (adresów, protokołów i portów) na podstawie nazw lub identyfikatorów innego typu.</span><span class="sxs-lookup"><span data-stu-id="378eb-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="378eb-104">W przeszłości rozpoznawania nazw równorzędnych o zostały skomplikowanym łączności z założenia przejściowy, a także innych braków w ramach systemu nazw domen (DNS).</span><span class="sxs-lookup"><span data-stu-id="378eb-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="378eb-105">Microsoft® Windows® sieci Peer-to-Peer platformy rozwiązuje ten problem z rozpoznawania protokołu PNRP (Peer Name), bezpieczna, skalowalna i dynamicznych rejestracji i protokołu rozpoznawania nazw zaprojektowane dla systemu Windows XP, a następnie uaktualnionego na Vista™ systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="378eb-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="378eb-106">Usługa PNRP działa bardzo różniący się od tradycyjnych protokołów rozpoznawania nazw, otwieranie ekscytujące nowe możliwości dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="378eb-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="378eb-107">Usłudze PNRP nazwy elementów równorzędnych może odnosić się do komputera, lub poszczególnych aplikacji lub usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="378eb-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="378eb-108">Rozpoznawanie nazw elementów równorzędnych obejmuje adres, port i prawdopodobnie Ładunek rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="378eb-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="378eb-109">Ten system zalety odporność na uszkodzenia, nie wąskich gardeł i nazwy rozwiązania, które nigdy nie zwróci stare adresy; wprowadzenie protokołu idealnym rozwiązaniem służącym do lokalizowania użytkowników mobilnych.</span><span class="sxs-lookup"><span data-stu-id="378eb-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="378eb-110">Pod względem zabezpieczeń, nazwy elementów równorzędnych może być publikowane jako zabezpieczonych (chronionej) lub niezabezpieczona (bez ochrony).</span><span class="sxs-lookup"><span data-stu-id="378eb-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="378eb-111">Usługa PNRP wykorzystuje kryptografię klucza publicznego do ochrony nazwy bezpiecznego elementów równorzędnych przed fałszowaniem; zarówno komputery i usługi mogą mieć nazwę w usłudze PNRP.</span><span class="sxs-lookup"><span data-stu-id="378eb-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
-   <span data-ttu-id="378eb-112">Protokołu rozpoznawania nazw równorzędnych przedstawiono następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="378eb-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="378eb-113">Rozproszone i prawie całkowicie niekorzystającą.</span><span class="sxs-lookup"><span data-stu-id="378eb-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="378eb-114">Serwery są tylko wymagane dla bootstrapping procesu.</span><span class="sxs-lookup"><span data-stu-id="378eb-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="378eb-115">Zabezpiecz nazwa publikacji bez udziału osób trzecich.</span><span class="sxs-lookup"><span data-stu-id="378eb-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="378eb-116">W przeciwieństwie do publikacji nazwy DNS publikowanie nazw PNRP jest natychmiastowe i bez ponoszenia kosztów finansowych.</span><span class="sxs-lookup"><span data-stu-id="378eb-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="378eb-117">Aktualizacje PNRP w czasie rzeczywistym, co uniemożliwia rozpoznawanie stare adresy.</span><span class="sxs-lookup"><span data-stu-id="378eb-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="378eb-118">Rozpoznawanie nazw za pomocą PNRP wykracza poza komputerów zezwalając również rozpoznawania nazw dla usług.</span><span class="sxs-lookup"><span data-stu-id="378eb-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="378eb-119">Namespace System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="378eb-119">The System.Net.PeerToPeer Namespace</span></span>  
  
-   <span data-ttu-id="378eb-120">Funkcje PNRP jest definiowana za pomocą <xref:System.Net.PeerToPeer> przestrzeni nazw w .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="378eb-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="378eb-121">Zapewnia zestaw typów, które mogą służyć do rejestrowania i rozpoznawania nazw równorzędnych o dostępności usługi PNRP.</span><span class="sxs-lookup"><span data-stu-id="378eb-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-  
  
-   <span data-ttu-id="378eb-122">(PNRP i mechanizmy rozpoznawania elementów równorzędnych niestandardowe można tworzyć i wystąpień typów przy użyciu dostępnych w <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw.)</span><span class="sxs-lookup"><span data-stu-id="378eb-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-  
  
-   <span data-ttu-id="378eb-123">Podstawowe typy używane do rejestrowania i rozpoznawania nazw w usłudze PNRP dostępne są następujące:</span><span class="sxs-lookup"><span data-stu-id="378eb-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-  
  
-   <span data-ttu-id="378eb-124"><xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępne chmurze usługi PNRP, w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="378eb-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <span data-ttu-id="378eb-125"><xref:System.Net.PeerToPeer.PeerName>: Określa nazwę elementu równorzędnego, który może służyć do rejestrowania i następnie rozpoznawania elementu równorzędnego w chmurze.</span><span class="sxs-lookup"><span data-stu-id="378eb-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <span data-ttu-id="378eb-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Określa rekord w chmurze usługi PNRP, który zawiera informacje o rejestracji dla elementu równorzędnego, w tym punktów końcowych sieci, w których można się skontaktować elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="378eb-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <span data-ttu-id="378eb-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji w celu nazwa elementu równorzędnego, łącznie z metody służące do uruchamiania i zatrzymywania rejestracji nazw elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="378eb-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <span data-ttu-id="378eb-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazw równorzędnych do jego punktów końcowych sieci, w tym synchroniczne i asynchroniczne metod rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="378eb-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
-  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="378eb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="378eb-129">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [<span data-ttu-id="378eb-130">Przykłady programowania w języku sieci</span><span class="sxs-lookup"><span data-stu-id="378eb-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="378eb-131">Technologia PeerToPeer próbki</span><span class="sxs-lookup"><span data-stu-id="378eb-131">PeerToPeer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179571)