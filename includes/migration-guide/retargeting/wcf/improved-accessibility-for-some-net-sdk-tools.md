---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858934"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Acessibilidade aprimorada para algumas ferramentas do SDK do .NET

|   |   |
|---|---|
|Detalhes|No SDK do .NET Framework 4.7.1, as ferramentas SvcConfigEditor.exe e SvcTraceViewer.exe foram melhoradas com a correção de vários problemas de acessibilidade. A maioria eram problemas pequenos como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente. Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão estas ferramentas de SDK mais acessíveis. Certamente, essas correções alteram alguns comportamentos anteriores, como a ordem do foco do teclado. Para obter todas as correções de acessibilidade nessas ferramentas, é possível adicionar o seguinte ao arquivo app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.1|
|Type|Redirecionando|
