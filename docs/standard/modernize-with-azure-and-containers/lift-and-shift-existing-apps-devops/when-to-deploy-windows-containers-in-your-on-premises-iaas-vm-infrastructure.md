---
title: "Podczas wdrażania systemu Windows kontenery w lokalnej infrastruktury maszyn wirtualnych IaaS"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Podczas wdrażania systemu Windows kontenery w lokalnej infrastruktury maszyn wirtualnych IaaS"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 91a53f8eafe896ffe41e3f9938dca2679b81f3d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure"></a><span data-ttu-id="fe63e-103">Podczas wdrażania systemu Windows kontenery w lokalnej infrastruktury maszyn wirtualnych IaaS</span><span class="sxs-lookup"><span data-stu-id="fe63e-103">When to deploy Windows Containers in your on-premises IaaS VM infrastructure</span></span>

-   <span data-ttu-id="fe63e-104">Twoja organizacja może nie być gotowy do przeniesienia do chmury, lub ją po prostu nie można przenieść do chmury, z przyczyn biznesowych.</span><span class="sxs-lookup"><span data-stu-id="fe63e-104">Your organization might not be ready to move to the cloud, or it might simply not be able to move to the cloud for a business reason.</span></span> <span data-ttu-id="fe63e-105">Ale nadal można uzyskać korzyści wynikające ze stosowania kontenery systemu Windows w własne centrach danych.</span><span class="sxs-lookup"><span data-stu-id="fe63e-105">But, you can still get the benefits of using Windows Containers in your own datacenters.</span></span>

-   <span data-ttu-id="fe63e-106">Konieczne może być pozostałych artefaktów, które są używane lokalnymi i które może spowolnić możesz podczas próby przeniesienia do chmury.</span><span class="sxs-lookup"><span data-stu-id="fe63e-106">You might have other artifacts that are being used on-premises, and which might slow you down when you try to move to the cloud.</span></span> <span data-ttu-id="fe63e-107">Na przykład zabezpieczeń lub uwierzytelniania zależności z lokalnego systemu Windows Server Active Directory lub innych zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fe63e-107">For example, security or authentication dependencies with on-premises Windows Server Active Directory, or any other on-premises asset.</span></span>

-   <span data-ttu-id="fe63e-108">Jeżeli możesz uruchomić przy użyciu systemu Windows kontenery dzisiaj, możesz wprowadzić migracji stopniowej do chmury jutro z znacznie lepszą miejsca.</span><span class="sxs-lookup"><span data-stu-id="fe63e-108">If you start using Windows Containers today, you can make a phased migration to the cloud tomorrow from a much better position.</span></span> <span data-ttu-id="fe63e-109">Kontenery systemu Windows staje się jednostką wdrożenia wszystkie chmury z nie blokady.</span><span class="sxs-lookup"><span data-stu-id="fe63e-109">Windows Containers is becoming a unit of deployment for any cloud, with no lock-in.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="fe63e-110">[Poprzednie](when-not-to-deploy-to-windows-containers.md)
[dalej](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="fe63e-110">[Previous](when-not-to-deploy-to-windows-containers.md)
[Next](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)</span></span>