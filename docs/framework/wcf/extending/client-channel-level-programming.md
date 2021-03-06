---
title: Programação de nível de canal cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797263"
---
# <a name="client-channel-level-programming"></a>Programação de nível de canal cliente
Este tópico descreve como gravar um aplicativo cliente do Windows Communication Foundation (WCF) sem usar a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> classe e seu modelo de objeto associado.  
  
## <a name="sending-messages"></a>Enviando mensagens  
 Para estar pronto para enviar mensagens e receber e processar respostas, as etapas a seguir são necessárias:  
  
1. Crie uma associação.  
  
2. Crie uma fábrica de canais.  
  
3. Crie um canal.  
  
4. Envie uma solicitação e leia a resposta.  
  
5. Feche todos os objetos de canal.  
  
#### <a name="creating-a-binding"></a>Criar uma associação  
 Semelhante ao caso de recebimento (consulte [programação de nível de canal de serviço](service-channel-level-programming.md)), o envio de mensagens começa pela criação de uma associação. Este exemplo cria um novo <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> e adiciona um <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sua coleção de elementos.  
  
#### <a name="building-a-channelfactory"></a>Criando uma ChannelFactory  
 Em vez de criar <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>um, desta vez, criamos um <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> chamando na associação em que o parâmetro de <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>tipo é. Enquanto ouvintes de canal são usados pelo lado que aguarda mensagens de entrada, as fábricas de canal são usadas pelo lado que inicia a comunicação para criar um canal. Assim como ouvintes de canal, as fábricas de canal devem ser abertas primeiro antes de poderem ser usadas.  
  
#### <a name="creating-a-channel"></a>Criando um canal  
 Em seguida, <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> chamamos para criar <xref:System.ServiceModel.Channels.IRequestChannel>um. Essa chamada pega o endereço do ponto de extremidade com o qual desejamos se comunicar usando o novo canal que está sendo criado. Assim que tivermos um canal, chamamos o Open nele para colocá-lo em um estado pronto para comunicação. Dependendo da natureza do transporte, essa chamada para Open pode iniciar uma conexão com o ponto de extremidade de destino ou pode não fazer nada na rede.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Enviando uma solicitação e lendo a resposta  
 Uma vez que temos um canal aberto, podemos criar uma mensagem e usar o método de solicitação do canal para enviar a solicitação e aguardar a resposta voltar. Quando esse método retorna, temos uma mensagem de resposta que podemos ler para descobrir qual foi a resposta do ponto de extremidade.  
  
#### <a name="closing-objects"></a>Fechando objetos  
 Para evitar vazamento de recursos, nós fechamos objetos usados nas comunicações quando não são mais necessários.  
  
 O exemplo de código a seguir mostra um cliente básico usando a fábrica de canais para enviar uma mensagem e ler a resposta.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
