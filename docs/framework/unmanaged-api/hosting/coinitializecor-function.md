---
title: "Função CoInitializeCor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeCor
helpviewer_keywords: CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 119a01a33faeedc49931f3e7cbb1685b26366d0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="coinitializecor-function"></a><span data-ttu-id="86c53-102">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="86c53-102">CoInitializeCor Function</span></span>
<span data-ttu-id="86c53-103">`CoInitializeCor` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="86c53-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86c53-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="86c53-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="86c53-105">Remarks</span></span>  
 <span data-ttu-id="86c53-106">Para inicializar o common language runtime, use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="86c53-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c53-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86c53-107">Requirements</span></span>  
 <span data-ttu-id="86c53-108">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86c53-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c53-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86c53-109">See Also</span></span>  
 [<span data-ttu-id="86c53-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="86c53-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)