---
title: IMetaDataEmit2::DefineMethodSpec 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce6df232f3793b8b61d9fa7c18c9c90ca9fa3900
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043689"
---
# <a name="imetadataemit2definemethodspec-method"></a>IMetaDataEmit2::DefineMethodSpec 方法
建立泛型方法的執行個體，並取得定義的語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a>參數  
 `tkParent`  
 [in]要建立一般的執行個體方法語彙基元。 語彙基元必須是型別`mdMethodDef`或`mdMemberRef`。  
  
 `pvSigBlob`  
 [in]二進位 COM + 方法的簽章指標。  
  
 `cbSibBlob`  
 [in]大小，以位元組為單位的`pvSigBlob`。  
  
 `pmi`  
 [out]方法的中繼資料簽章定義的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
