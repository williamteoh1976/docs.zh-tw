---
title: IMethodMalloc 介面
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969802"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc 介面
提供方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。  
  
> [!NOTE]
>  `IMethodMalloc`介面是簡單的記憶體配置器。 它可讓您配置記憶體，但不是能釋放它。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|嘗試為新的 MSIL 函式主體配置指定的記憶體數量。|  
  
## <a name="remarks"></a>備註  
 每個配置器為特定模組，並確保函式主體會從模組的基底的正面位移。 以上的模組基底的記憶體可能寶貴，因此配置器應該用來只為函式主體配置記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
