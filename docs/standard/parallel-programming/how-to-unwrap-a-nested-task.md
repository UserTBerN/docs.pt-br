---
title: Como desencapsular uma tarefa aninhada
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106903"
---
# <a name="how-to-unwrap-a-nested-task"></a>Como desencapsular uma tarefa aninhada
Você pode retornar uma tarefa de um método e esperar ou continuar a tarefa, conforme é mostrado no exemplo a seguir:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 No exemplo anterior, a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é do tipo `string` (`String` no Visual Basic).  
  
 No entanto, em alguns cenários, pode ser pertinente criar uma tarefa dentro de outra tarefa e, em seguida, retornar a tarefa aninhada. Nesse caso, o `TResult` da tarefa delimitadora é uma tarefa. No exemplo a seguir, a propriedade Result é um `Task<Task<string>>` em C# ou `Task(Of Task(Of String))` no Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Embora seja possível gravar código para decodificar a tarefa externa e recuperar a tarefa original e sua propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>, esse código não é fácil escrever porque você deve lidar com exceções e solicitações de cancelamento. Nessa situação, é recomendável que você use um dos métodos de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, conforme é mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Os métodos <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> podem ser usados para transformar qualquer `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` no Visual Basic) em um `Task` ou `Task<TResult>` (`Task(Of TResult)` no Visual Basic). A nova tarefa representa por completo a tarefa aninhada interna e inclui o estado de cancelamento e todas as exceções.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar os métodos de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Programação Assíncrona baseada em tarefas](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
