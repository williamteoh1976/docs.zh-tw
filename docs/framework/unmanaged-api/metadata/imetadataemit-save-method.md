---
title: IMetaDataEmit::Save 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49e45085b0fbca10e490f11ce588f68aa8237b46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043052"
---
# <a name="imetadataemitsave-method"></a>IMetaDataEmit::Save 方法
將所有的中繼資料儲存在指定的位址檔案目前的範圍中。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wzFile`  
 [in]若要將儲存至檔案的名稱。 如果此值是 null，記憶體中複本會儲存到最後一個使用的位置。  
  
 `dwSaveFlags`  
 [in] 保留。 必須是零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
