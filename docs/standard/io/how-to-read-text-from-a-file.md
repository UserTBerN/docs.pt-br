---
title: 'Como: Ler texto de um arquivo'
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155718"
---
# <a name="how-to-read-text-from-a-file"></a>Como: Ler texto de um arquivo
Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho. Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo.
  
> [!NOTE]
> Esses exemplos de código não se aplicam ao desenvolvimento para aplicativos UWP (Universal do Windows) porque o Windows Runtime fornece diferentes tipos de fluxos para leitura e gravação em arquivos. Para um exemplo que mostra como ler texto de um arquivo em um aplicativo UWP, consulte [Quickstart: Leitura e escrita de arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Para exemplos que mostram como converter entre fluxos .NET Framework e fluxos de execução do Windows, consulte [Como: Converter entre fluxos .NET Framework e fluxos de execução do Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Exemplo: Leitura síncrona em um aplicativo de console  
O exemplo a seguir mostra uma operação de leitura síncrona em um aplicativo de console. Esse exemplo abre o arquivo de texto usando um leitor de fluxo, copia o conteúdo para uma cadeia de caracteres e gera a cadeia de caracteres no console.  
  
> [!IMPORTANT]
> O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Exemplo: Leitura assíncrona em um aplicativo WPF
 O exemplo a seguir mostra uma operação de leitura assíncrona em um aplicativo WPF (Windows Presentation Foundation).  
  
> [!IMPORTANT]
> O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [I/O do arquivo assíncrono](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Como: Criar uma listagem de diretórios](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Início rápido: ler e gravar arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Como: Converter entre fluxos .NET Framework e fluxos de tempo de execução do Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Como: Abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como: Escrever texto para um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: Ler caracteres de uma seqüência](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Como: Escrever caracteres em uma seqüência](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
