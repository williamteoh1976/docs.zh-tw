---
title: ICorDebugNativeFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd16db8c009fe81f2674a8bf9c7ad3a2a4827777
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927311"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP 方法
取得 HRESULT，指出是否以原生程式碼中，設定為指定的位移位置的指令指標 (IP) 安全。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `nOffset`  
 [in]指令指標所需的設定。  
  
## <a name="remarks"></a>備註  
 使用`CanSetIP`方法之前呼叫[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)方法。 如果`CanSetIP`會傳回任何 HRESULT 以外 s_ok 時，您可以仍然叫用`ICorDebugNativeFrame::SetIP`，但不偵錯工具，將會繼續進行偵錯程式碼的安全且正確執行的保證。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
