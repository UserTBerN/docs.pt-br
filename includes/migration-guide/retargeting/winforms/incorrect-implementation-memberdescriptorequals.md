---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859314"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Implementação incorreta de MemberDescriptor.Equals

|   |   |
|---|---|
|Detalhes|A implementação original do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> compara duas propriedades de cadeia de caracteres diferentes dos objetos que estão sendo comparados: o nome da categoria e a cadeia de caracteres de descrição. A correção é para comparar o <xref:System.ComponentModel.MemberDescriptor.Category> do primeiro objeto com o <xref:System.ComponentModel.MemberDescriptor.Category> de um segundo objeto, e o <xref:System.ComponentModel.MemberDescriptor.Description> do primeiro com o <xref:System.ComponentModel.MemberDescriptor.Description> do segunda.|
|Sugestão|Se seu aplicativo depende do <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> e, às vezes, retorna <code>false</code> quando os descritores são equivalentes, e você está direcionado ao .NET Framework 4.6.2 ou posterior, há várias opções:<ol><li>Fazer alterações no código para comparar os campos <xref:System.ComponentModel.MemberDescriptor.Category> e <xref:System.ComponentModel.MemberDescriptor.Description> manualmente além de chamar o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.</li><li>Recuse essa alteração adicionando o seguinte valor ao arquivo app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Se seu aplicativo for direcionado ao NET Framework 4.6.1 ou anterior e executado no .NET Framework 4.6.2 ou posterior e você quiser que essa alteração seja habilitada, defina a opção de compatibilidade como <code>false</code> adicionando o seguinte valor ao arquivo app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|
