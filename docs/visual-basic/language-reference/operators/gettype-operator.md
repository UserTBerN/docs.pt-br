---
title: Operador GetType
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349544"
---
# <a name="gettype-operator-visual-basic"></a>Operador GetType (Visual Basic)
Retorna um objeto <xref:System.Type> para o tipo especificado. O objeto <xref:System.Type> fornece informações sobre o tipo, como suas propriedades, métodos e eventos.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---|---|  
|`typename`|O nome do tipo para o qual você deseja informações.|  
  
## <a name="remarks"></a>Comentários  
 O operador `GetType` retorna o objeto <xref:System.Type> para o `typename`especificado. Você pode passar o nome de qualquer tipo definido em `typename`. Isso inclui o seguinte:  
  
- Qualquer tipo de dados Visual Basic, como `Boolean` ou `Date`.  
  
- Qualquer .NET Framework classe, estrutura, módulo ou interface, como <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.  
  
- Qualquer classe, estrutura, módulo ou interface definida pelo seu aplicativo.  
  
- Qualquer matriz definida pelo seu aplicativo.  
  
- Qualquer delegado definido pelo seu aplicativo.  
  
- Qualquer Enumeração definida por Visual Basic, o .NET Framework ou seu aplicativo.  
  
 Se você quiser obter o objeto de tipo de uma variável de objeto, use o método <xref:System.Type.GetType%2A?displayProperty=nameWithType>.  
  
 O operador `GetType` pode ser útil nas seguintes circunstâncias:  
  
- Você deve acessar os metadados para um tipo em tempo de execução. O objeto <xref:System.Type> fornece metadados como membros de tipo e informações de implantação. Você precisa disso, por exemplo, para refletir sobre um assembly. Para obter mais informações, consulte <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Você deseja comparar duas referências de objeto para ver se elas se referem a instâncias do mesmo tipo. Se isso for feito, `GetType` retornará referências ao mesmo objeto <xref:System.Type>.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram o operador de `GetType` em uso.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Consulte também

- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
