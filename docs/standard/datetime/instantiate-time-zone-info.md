---
title: "Porady: Tworzenie wystąpień obiektów TimeZoneInfo"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="0c996-102">Porady: Tworzenie wystąpień obiektów TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="0c996-102">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="0c996-103">Typowym sposobem tworzenia wystąpienia <xref:System.TimeZoneInfo> obiekt jest można pobrać z rejestru informacji o nim.</span><span class="sxs-lookup"><span data-stu-id="0c996-103">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="0c996-104">W tym temacie opisano sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0c996-104">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="0c996-105">Aby Tworzenie wystąpień obiektów TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="0c996-105">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="0c996-106">Deklarowanie <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c996-106">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="0c996-107">Wywołanie `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0c996-107">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="0c996-108">Obsługa wszelkie wyjątki zgłaszane przez metodę, szczególnie <xref:System.TimeZoneNotFoundException> który jest generowany, jeśli strefa czasowa nie jest zdefiniowana w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="0c996-108">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="0c996-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c996-109">Example</span></span>

<span data-ttu-id="0c996-110">Poniższy kod pobiera <xref:System.TimeZoneInfo> obiekt, który reprezentuje Eastern Standard strefę czasową i wyświetla wschodni czas standardowy, która odpowiada na czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="0c996-110">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="0c996-111"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Jednego parametru metody to identyfikator strefy czasowej, która ma zostać pobrane, co odpowiada obiektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0c996-111">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0c996-112">Identyfikator strefy czasowej jest pole klucza, który unikatowo identyfikuje strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="0c996-112">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="0c996-113">Mimo że większość klawiszy jest stosunkowo krótkich, identyfikator strefy czasowej jest stosunkowo długo.</span><span class="sxs-lookup"><span data-stu-id="0c996-113">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="0c996-114">W większości przypadków, jego wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A> właściwość <xref:System.TimeZoneInfo> obiektu, który jest używany do określenia nazwy strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="0c996-114">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="0c996-115">Istnieją wyjątki.</span><span class="sxs-lookup"><span data-stu-id="0c996-115">However, there are exceptions.</span></span> <span data-ttu-id="0c996-116">Najlepszym sposobem, aby upewnić się, że należy podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępna w systemie i zanotuj identyfikatory stref czasowych na nich.</span><span class="sxs-lookup"><span data-stu-id="0c996-116">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="0c996-117">Aby zapoznać się z ilustracją, zobacz [porady: wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="0c996-117">For an illustration, see [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span></span> <span data-ttu-id="0c996-118">[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) temat zawiera także listę identyfikatorów wybranej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="0c996-118">The [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="0c996-119">Jeśli zostanie znaleziony strefy czasowej, metoda zwraca jego <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c996-119">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="0c996-120">Jeśli strefa czasowa nie zostanie znaleziony, metoda wygeneruje <xref:System.TimeZoneNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="0c996-120">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="0c996-121">Jeśli nie znaleziono strefę czasową, ale jego dane są uszkodzone lub niekompletne, metoda wygeneruje <xref:System.InvalidTimeZoneException>.</span><span class="sxs-lookup"><span data-stu-id="0c996-121">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="0c996-122">Jeśli aplikacja opiera się na strefę czasową, który musi być obecny, należy najpierw wywołać <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody można pobrać z rejestru informacji o strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="0c996-122">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="0c996-123">W przypadku niepowodzenia wywołania metody programu obsługi wyjątków należy następnie utwórz nowe wystąpienie klasy strefę czasową lub ponownie utworzyć przez deserializacja serializowanych <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c996-123">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="0c996-124">Zobacz [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) przykład.</span><span class="sxs-lookup"><span data-stu-id="0c996-124">See [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c996-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c996-125">See also</span></span>

<span data-ttu-id="0c996-126">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md)</span><span class="sxs-lookup"><span data-stu-id="0c996-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)</span></span>