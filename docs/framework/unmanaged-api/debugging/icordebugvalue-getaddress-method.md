---
title: Método ICorDebugValue::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 906ca2540e421953b3ce39300aa7b2376f789929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137096"
---
# <a name="icordebugvaluegetaddress-method"></a>Método ICorDebugValue::GetAddress
Obtém o endereço desse objeto "ICorDebugValue", que está no processo de ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAddress`  
 fora Ponteiro para um objeto `CORDB_ADDRESS` que especifica o endereço desse objeto de valor.  
  
## <a name="remarks"></a>Comentários  
 Se o valor não estiver disponível, será retornado 0 (zero). Isso pode acontecer se o valor for pelo menos parcialmente em registros ou armazenado em um identificador de coletor de lixo (`GCHandle`).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
