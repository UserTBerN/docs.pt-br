---
title: Cláusula let – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173582"
---
# <a name="let-clause-c-reference"></a>Cláusula let (Referência de C#)

Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá-lo em cláusulas subsequentes. É possível fazer isso com a palavra-chave `let`, que cria uma nova variável de intervalo e a inicializa com o resultado da expressão fornecida. Depois de inicializado com um valor, a variável de intervalo não pode ser usada para armazenar outro valor. No entanto, se a variável de intervalo mantiver um tipo passível de consulta, ela poderá ser consultada.

## <a name="example"></a>Exemplo

No exemplo a seguir, `let` é usado de duas maneiras:

1. Para criar um tipo enumerável que pode ser pesquisado por si só.

2. Para permitir que a consulta chame `ToLower` apenas uma vez na variável de intervalo `word`. Sem usar `let`, seria necessário chamar `ToLower` em cada predicado na cláusula `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Confira também

- [C# Referência](../../language-reference/index.md)
- [Palavras-chave de consulta (LINQ)](query-keywords.md)
- [LINQ em C#](../../linq/index.md)
- [Consulta Integrada ao Idioma (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Manipular exceções em expressões de consultas](../../linq/handle-exceptions-in-query-expressions.md)
