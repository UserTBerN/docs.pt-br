---
title: Erro ao carregar DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329555"
---
# <a name="error-in-loading-dll-visual-basic"></a>Erro no carregamento da DLL (Visual Basic)
Uma DLL (biblioteca de vínculo dinâmico) é uma biblioteca especificada na cláusula `Lib` de uma instrução `Declare`. Possíveis causas desse erro incluem:  
  
- O arquivo não é executável de DLL.  
  
- O arquivo não é uma DLL do Microsoft Windows.  
  
- A DLL faz referência a outra DLL que não está presente.  
  
- A DLL ou a DLL referenciada não está em um diretório especificado no caminho.  
  
## <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Se o arquivo for um arquivo de texto de origem e, portanto, não executável de DLL, ele deverá ser compilado e vinculado a um formulário executável DLL.  
  
- Se o arquivo não for uma DLL do Microsoft Windows, obtenha o equivalente do Microsoft Windows.  
  
- Se a DLL fizer referência a outra DLL que não está presente, obtenha a DLL referenciada e torne-a disponível.  
  
- Se a dll ou a DLL referenciada não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
