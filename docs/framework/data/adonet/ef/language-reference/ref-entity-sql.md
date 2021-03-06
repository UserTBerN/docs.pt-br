---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149941"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Retorna uma referência a uma instância de entidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Qualquer expressão válida que produzir uma instância de um tipo de objeto.  
  
## <a name="return-value"></a>Valor retornado  
 Uma referência à instância de entidade especificada.  
  
## <a name="remarks"></a>Comentários  
 Uma referência de entidade consiste da chave de entidade e um nome de conjunto de entidades. Porque os conjuntos de entidades diferentes podem ser baseados no mesmo tipo de entidade, uma chave específica de entidade pode aparecer em vários conjuntos de entidades. No entanto, uma referência de entidade é sempre exclusivo. Se a expressão de entrada representa um objeto armazenado, uma referência a essa entidade será retornada. Se a expressão de entrada não é uma entidade armazenado, uma referência nula será retornada.  
  
 Se o operador de extração de propriedade (.) é usada para acessar uma propriedade de uma entidade, a referência é desreferenciada automaticamente.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador de referência para retornar a referência para um argumento de entidade de entrada. A mesma consulta desreferencia a referência porque estamos usando uma operação de extração de propriedade (.) para acessar uma propriedade de entidade do produto. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [Como: Executar uma consulta que retorna resultados do PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Confira também

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [Chave](key-entity-sql.md)
- [Referência de Entity SQL](entity-sql-reference.md)
- [Definições de tipo](type-definitions-entity-sql.md)
