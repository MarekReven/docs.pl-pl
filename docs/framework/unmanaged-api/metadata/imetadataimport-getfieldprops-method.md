---
title: "IMetaDataImport::GetFieldProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d5874169e0f8c452b177309702444ea84858557e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="ca7a2-102">IMetaDataImport::GetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca7a2-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="ca7a2-103">Pobiera metadane skojarzone z polem odwołuje się określony FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca7a2-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca7a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca7a2-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ca7a2-106">[in] Token FieldDef, który reprezentuje pole, aby pobrać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ca7a2-107">[out] Wskaźnik do tokenu — TypeDef, który reprezentuje typ pola należącego do klasy.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="ca7a2-108">[out] Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="ca7a2-109">[in] Rozmiar w znaki dwubajtowe buforu dla *szField*.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="ca7a2-110">[out] Rzeczywisty rozmiar buforu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ca7a2-111">[out] Flagi skojarzone z metadanymi pola.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ca7a2-112">[in] Wskaźnik do wartości binarne metadanych, opisujący pola.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ca7a2-113">[out] Wyrażony w bajtach rozmiar `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ca7a2-114">[out] Flaga, która określa typ wartości pola.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ca7a2-115">[out] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ca7a2-116">[out] Rozmiar znaków z `ppValue`, lub zero, jeśli ciąg nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ca7a2-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca7a2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca7a2-117">Requirements</span></span>  
 <span data-ttu-id="ca7a2-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca7a2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca7a2-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca7a2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca7a2-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca7a2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca7a2-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca7a2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7a2-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca7a2-122">See Also</span></span>  
 [<span data-ttu-id="ca7a2-123">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="ca7a2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ca7a2-124">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ca7a2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)