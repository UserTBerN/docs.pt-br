---
title: 'Como: criar fusos horários sem regras de ajuste'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 344d8307318d5a2e50eddb39ef488cd8c5f2fdac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129089"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Como: criar fusos horários sem regras de ajuste

As informações precisas de fuso horário exigidas por um aplicativo podem não estar presentes em um sistema específico por vários motivos:

- O fuso horário nunca foi definido no registro do sistema local.

- Os dados sobre o fuso horário foram modificados ou removidos do registro.

- O fuso horário existe, mas não tem informações precisas sobre os ajustes de fuso horário de um período histórico específico.

Nesses casos, você pode chamar o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> para definir o fuso horário exigido pelo seu aplicativo. Você pode usar as sobrecargas desse método para criar um fuso horário com ou sem regras de ajuste. Se o fuso horário der suporte ao horário de verão, você poderá definir ajustes com regras de ajuste fixos ou flutuantes. (Para obter as definições desses termos, consulte a seção "terminologia de fuso horário" em [visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Os fusos horários personalizados criados chamando o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> não são adicionados ao registro. Em vez disso, eles podem ser acessados somente por meio da referência de objeto retornada pela chamada do método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.

Este tópico mostra como criar um fuso horário sem regras de ajuste. Para criar um fuso horário que dê suporte às regras de ajuste de horário de verão, consulte [como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Para criar um fuso horário sem regras de ajuste

1. Defina o nome de exibição do fuso horário.

   O nome de exibição segue um formato bastante padrão no qual o deslocamento do fuso horário do UTC (tempo Universal Coordenado) é incluído entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais cidades no fuso horário ou um ou mais dos cou ntries ou regiões no fuso horário.

2. Defina o nome do horário padrão do fuso horário. Normalmente, essa cadeia de caracteres também é usada como o identificador do fuso horário.

3. Se você quiser usar um identificador diferente do nome padrão do fuso horário, defina o identificador de fuso horário.

4. Crie uma instância de um objeto <xref:System.TimeSpan> que define o deslocamento do fuso horário do UTC. Fusos horários com horas posteriores a UTC têm um deslocamento positivo. Fusos horários com horários que são anteriores ao UTC têm um deslocamento negativo.

5. Chame o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> para instanciar o novo fuso horário.

## <a name="example"></a>Exemplo

O exemplo a seguir define um fuso horário personalizado para Mawson, Antártica, que não tem nenhuma regra de ajuste.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

A cadeia de caracteres atribuída à propriedade <xref:System.TimeZoneInfo.DisplayName%2A> segue um formato padrão no qual o deslocamento do fuso horário do UTC é seguido por uma descrição amigável do fuso horário.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que os seguintes namespaces sejam importados:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
