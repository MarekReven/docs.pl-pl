---
title: "Usuwanie funkcji (niezarządzany wykaz interfejsów API)"
description: "Funkcja usuwania usuwa określonej właściwości i wszystkie jego kwalifikatory z definicji klasy modelu wspólnych informacji."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f32487d2bd59bd76acdc32218c6bb0842de20e87
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="delete-function"></a><span data-ttu-id="87f0f-103">Usuń — funkcja</span><span class="sxs-lookup"><span data-stu-id="87f0f-103">Delete function</span></span>
<span data-ttu-id="87f0f-104">Usuwa określonej właściwości i wszystkie jego kwalifikatory z definicji klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="87f0f-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="87f0f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="87f0f-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="87f0f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87f0f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="87f0f-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="87f0f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="87f0f-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="87f0f-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="87f0f-109">[in] Nazwa właściwości do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="87f0f-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="87f0f-110">`wszName`musi być wskaźnikiem do prawidłowej `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="87f0f-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="87f0f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87f0f-111">Return value</span></span>

<span data-ttu-id="87f0f-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="87f0f-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="87f0f-113">Stała</span><span class="sxs-lookup"><span data-stu-id="87f0f-113">Constant</span></span>  |<span data-ttu-id="87f0f-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="87f0f-114">Value</span></span>  |<span data-ttu-id="87f0f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="87f0f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="87f0f-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="87f0f-116">0x80041001</span></span> | <span data-ttu-id="87f0f-117">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="87f0f-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="87f0f-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="87f0f-118">0x80041016</span></span> | <span data-ttu-id="87f0f-119">Nie można usunąć właściwości.</span><span class="sxs-lookup"><span data-stu-id="87f0f-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="87f0f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="87f0f-120">0x80041008</span></span> | <span data-ttu-id="87f0f-121">`wszzName` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="87f0f-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="87f0f-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="87f0f-122">0x80041002</span></span> | <span data-ttu-id="87f0f-123">Określona właściwość nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="87f0f-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="87f0f-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="87f0f-124">0x80041006</span></span> | <span data-ttu-id="87f0f-125">Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="87f0f-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="87f0f-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="87f0f-126">0x8004101c</span></span> | <span data-ttu-id="87f0f-127">Właściwość jest dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="87f0f-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="87f0f-128">Właściwość jest właściwością systemu.</span><span class="sxs-lookup"><span data-stu-id="87f0f-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="87f0f-129">0</span><span class="sxs-lookup"><span data-stu-id="87f0f-129">0</span></span> | <span data-ttu-id="87f0f-130">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87f0f-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="87f0f-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="87f0f-131">0x80041030</span></span> | <span data-ttu-id="87f0f-132">Funkcja usunąć zastąpienie wartości domyślne dla bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="87f0f-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="87f0f-133">Wartość domyślna tej właściwości w klasie nadrzędnej została reactiviated.</span><span class="sxs-lookup"><span data-stu-id="87f0f-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="87f0f-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87f0f-134">Remarks</span></span>

<span data-ttu-id="87f0f-135">Ta funkcja jest zawijana wywołanie [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="87f0f-135">This function wraps a call to the [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="87f0f-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87f0f-136">Requirements</span></span>  
 <span data-ttu-id="87f0f-137">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f0f-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f0f-138">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="87f0f-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="87f0f-139">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87f0f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f0f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87f0f-140">See also</span></span>  
[<span data-ttu-id="87f0f-141">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="87f0f-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)