---
title: ICorDebugAssembly 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645523"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly 介面

表示組件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateModules 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|取得組件中所包含之模組的列舉值。|  
|[GetAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|取得包含這個應用程式定義域的介面指標`ICorDebugAssembly`執行個體。|  
|[GetCodeBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|不在目前版本的.NET framework 中實作。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|取得組件名稱。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|取得 ICorDebugProcess 執行個體執行所在的組件。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
