---
title: "213 — ServiceHostStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61d79adce71be9ef93e9232e01a8cba5f5319f79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="c3d7a-102">213 — ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="c3d7a-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="c3d7a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3d7a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3d7a-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3d7a-104">ID</span></span>|<span data-ttu-id="c3d7a-105">213</span><span class="sxs-lookup"><span data-stu-id="c3d7a-105">213</span></span>|  
|<span data-ttu-id="c3d7a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c3d7a-106">Keywords</span></span>|<span data-ttu-id="c3d7a-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="c3d7a-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="c3d7a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3d7a-108">Level</span></span>|<span data-ttu-id="c3d7a-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="c3d7a-109">LogAlways</span></span>|  
|<span data-ttu-id="c3d7a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c3d7a-110">Channel</span></span>|<span data-ttu-id="c3d7a-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="c3d7a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3d7a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d7a-112">Description</span></span>  
 <span data-ttu-id="c3d7a-113">To zdarzenie jest emitowany po uruchomieniu hosta usługi hostowanej w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="c3d7a-114">Dzieje się tak zazwyczaj, gdy usługa jest aktywowany przez komunikat.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="c3d7a-115">Może się również zdarzyć, jeśli usługa jest skonfigurowana do automatycznego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3d7a-116">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c3d7a-116">Message</span></span>  
 <span data-ttu-id="c3d7a-117">Rozpoczęto ServiceHost: "%1".</span><span class="sxs-lookup"><span data-stu-id="c3d7a-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3d7a-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c3d7a-118">Details</span></span>  
  
|<span data-ttu-id="c3d7a-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3d7a-119">Data Item Name</span></span>|<span data-ttu-id="c3d7a-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3d7a-120">Data Item Type</span></span>|<span data-ttu-id="c3d7a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d7a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3d7a-122">Nazwa typu usługi</span><span class="sxs-lookup"><span data-stu-id="c3d7a-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="c3d7a-123">Element FullName CLR typu implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="c3d7a-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="c3d7a-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="c3d7a-125">Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c3d7a-126">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="c3d7a-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c3d7a-127">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="c3d7a-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c3d7a-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c3d7a-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c3d7a-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c3d7a-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|