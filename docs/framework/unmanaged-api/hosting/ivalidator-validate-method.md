---
title: "IValidator::Validate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 722c6acc7e152a78ba28bc2730b2fdc7e0c45eb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="7072e-102">IValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="7072e-102">IValidator::Validate Method</span></span>
<span data-ttu-id="7072e-103">Weryfikuje określony przenośny plik wykonywalny (PE) lub plik języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7072e-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7072e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7072e-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7072e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7072e-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="7072e-106">[in] Wskaźnik do `IVEHandler` wystąpienie, które obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7072e-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="7072e-107">[in] Wskaźnik do ładowania pliku domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7072e-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="7072e-108">[in] Bitowe połączenie [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości i wskazujący operacji sprawdzania poprawności, które powinny zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="7072e-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="7072e-109">[in] Maksymalna liczba błędów umożliwia przed zakończeniem sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7072e-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="7072e-110">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="7072e-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="7072e-111">[in] Ciąg określający nazwę pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="7072e-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="7072e-112">[in] Wskaźnik do bufora pamięci, w którym przechowywany jest plik.</span><span class="sxs-lookup"><span data-stu-id="7072e-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="7072e-113">[in] Rozmiar w bajtach, pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="7072e-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7072e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7072e-114">Requirements</span></span>  
 <span data-ttu-id="7072e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7072e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7072e-116">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="7072e-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7072e-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7072e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7072e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7072e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7072e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7072e-119">See Also</span></span>  
 