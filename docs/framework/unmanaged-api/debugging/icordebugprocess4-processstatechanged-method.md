---
title: ICorDebugProcess4::ProcessStateChanged 方法
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378986"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="bbc2f-102">ICorDebugProcess4::ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="bbc2f-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="bbc2f-103">通知 ICorDebug 管線外的處理序偵錯工具會繼續偵錯的項目執行。</span><span class="sxs-lookup"><span data-stu-id="bbc2f-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbc2f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bbc2f-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="bbc2f-105">參數</span><span class="sxs-lookup"><span data-stu-id="bbc2f-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="bbc2f-106">[in]成員[CorDebugStateChange 列舉](cordebugstatechange-enumeration.md)描述處理程序的執行狀態變更。</span><span class="sxs-lookup"><span data-stu-id="bbc2f-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbc2f-107">備註</span><span class="sxs-lookup"><span data-stu-id="bbc2f-107">Remarks</span></span>

<span data-ttu-id="bbc2f-108">提供的方法是一部分`ICorDebugProcess4`介面，而對應的虛擬方法表的第四個插槽。</span><span class="sxs-lookup"><span data-stu-id="bbc2f-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbc2f-109">需求</span><span class="sxs-lookup"><span data-stu-id="bbc2f-109">Requirements</span></span>

 <span data-ttu-id="bbc2f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc2f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bbc2f-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="bbc2f-111">**Header:** None</span></span>

 <span data-ttu-id="bbc2f-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="bbc2f-112">**Library:** None</span></span>
 
 <span data-ttu-id="bbc2f-113">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbc2f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc2f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbc2f-114">See also</span></span>

- [<span data-ttu-id="bbc2f-115">ICorDebugProcess4 介面</span><span class="sxs-lookup"><span data-stu-id="bbc2f-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="bbc2f-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bbc2f-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bbc2f-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="bbc2f-117">Debugging</span></span>](index.md)