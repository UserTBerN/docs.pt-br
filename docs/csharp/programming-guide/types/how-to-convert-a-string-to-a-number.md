---
title: Como converter uma seqüência de string sem um número - C# Guia de Programação
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 54a4562a5cc493fc287bdf2f6bcf9723557f2a05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157033"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Como converter uma string para um número (C# Programming Guide)

Você pode converter uma [string](../../language-reference/builtin-types/reference-types.md) para `Parse` `TryParse` um número chamando o ou`int` `long`método `double`encontrado nos vários tipos numéricos (, , etc.), ou usando métodos na <xref:System.Convert?displayProperty=nameWithType> classe.  
  
 Se você tiver uma string, é um pouco `TryParse` mais eficiente [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)e `Parse` simples chamar um [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)método (por exemplo, ) ou método (por exemplo, ).  Usar um método <xref:System.Convert> é mais útil para objetos gerais que implementam <xref:System.IConvertible>.  
  
 É possível usar métodos `Parse` ou `TryParse` no tipo numérico que se espera que a cadeia de caracteres contenha, como o tipo <xref:System.Int32?displayProperty=nameWithType>.  O método <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> usa <xref:System.Int32.Parse%2A> internamente.  O `Parse` método retorna o número convertido; o `TryParse` método <xref:System.Boolean> retorna um valor que indica se a conversão foi bem sucedida e retorna o número convertido em um [ `out` parâmetro](../../language-reference/keywords/out.md). Se a seqüência não `Parse` estiver em um `TryParse` formato `false`válido, lança uma exceção, enquanto retorna . Ao chamar um método `Parse`, você sempre deve usar o tratamento de exceções para capturar um <xref:System.FormatException> no caso da operação de análise falhar.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Como chamar os métodos Parse e TryParse

Os métodos `Parse` e `TryParse` ignoram o espaço em branco no início e no final da cadeia de caracteres; porém, todos os outros caracteres devem formar o tipo numérico correto (`int`, `long`, `ulong`, `float`, `decimal` etc.).  Qualquer espaço em branco na cadeia de caracteres que forma o número causa um erro.  Por exemplo, é possível usar `decimal.TryParse` para analisar "10", "10,3" ou "  10  ", mas não é possível usar esse método para analisar 10 de "10X", "1 0" (observe o espaço inserido), "10 .3" (observe o espaço inserido), "10e1" (`float.TryParse` funcionará neste caso) e assim por diante. Além disso, uma cadeia de caracteres cujo valor seja `null` ou <xref:System.String.Empty?displayProperty=nameWithType> falhará ao ser analisada com êxito. Você pode verificar uma cadeia de caracteres nula ou vazia antes de tentar analisá-la chamando o método <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>.

O exemplo a seguir demonstra chamadas com e sem êxito para `Parse` e `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

O exemplo a seguir ilustra uma abordagem para analisar uma cadeia de caracteres que deve incluir caracteres numéricos à esquerda (incluindo caracteres hexadecimais) e caracteres não numéricos à direita. Ele atribui caracteres válidos do início de uma cadeia de caracteres até uma nova cadeia de caracteres antes de chamar o método <xref:System.Int32.TryParse%2A>. Como as cadeias de caracteres a ser analisadas contêm um pequeno número de caracteres, o exemplo chama o método <xref:System.String.Concat%2A?displayProperty=nameWithType> para atribuir os caracteres válidos em uma nova cadeia de caracteres. Para cadeias de caracteres maiores, pode ser usada a classe <xref:System.Text.StringBuilder>.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Chamar os métodos de conversão

A tabela a seguir lista alguns dos métodos da classe <xref:System.Convert> que podem ser usados para converter uma cadeia de caracteres em um número.  
  
|Tipo numérico|Método|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 O exemplo a <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> seguir chama o método de converter uma seqüência de entrada em um [int](../../language-reference/builtin-types/integral-numeric-types.md). O exemplo captura as duas exceções mais comuns <xref:System.FormatException> <xref:System.OverflowException>que podem ser lançadas por este método, e . Se o número resultante puder ser incrementado sem exceder <xref:System.Int32.MaxValue?displayProperty=nameWithType>, o exemplo adicionará 1 ao resultado e exibirá a saída.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Confira também

- [Tipos](./index.md)
- [Como determinar se uma cadeia de caracteres representa um valor numérico](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Amostra: Utilitário de Formatação do WinForms do .NET Core (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
