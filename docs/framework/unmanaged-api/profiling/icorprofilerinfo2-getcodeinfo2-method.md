---
title: Método ICorProfilerInfo2::GetCodeInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 9295ea8b22f72529f55cbe13f6a79a0aa34d2fa0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868757"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>Método ICorProfilerInfo2::GetCodeInfo2
Obtém as extensões do código nativo associado ao `FunctionID`especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionID`  
 no A ID da função à qual o código nativo está associado.  
  
 `cCodeInfos`  
 no O tamanho da matriz de `codeInfos`.  
  
 `pcCodeInfos`  
 fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.  
  
 `codeInfos`  
 fora Um buffer fornecido pelo chamador. Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 As extensões são classificadas em ordem de aumento do deslocamento da MSIL (Microsoft Intermediate Language).  
  
 Depois que `GetCodeInfo2` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de `COR_PRF_CODE_INFO`. Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`. Se `cCodeInfos` dividido pelo tamanho de uma estrutura de `COR_PRF_CODE_INFO` for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo2` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de `COR_PRF_CODE_INFO` e chamar `GetCodeInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
