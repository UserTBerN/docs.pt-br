---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859356"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>Agora, RSACng carrega corretamente as chaves RSA de tamanho não padrão

|   |   |
|---|---|
|Detalhes|Nas versões do .NET Framework anteriores a 4.6.2, os clientes com tamanhos de chave não padrão para certificados RSA não conseguiam acessá-las por meio dos métodos de extensão <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> e <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>.  Uma <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> com uma mensagem &quot;O tamanho de chave solicitado não é compatível&quot; é gerada. Esse problema foi corrigido no .NET Framework 4.6.2. Da mesma forma, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> e <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> agora funcionam com tamanhos de chave não padrão sem gerar um <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Sugestão|Se houver qualquer lógica de tratamento de exceções dependente do comportamento anterior, em que um <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> é gerado quando tamanhos de chave não padrão são usados, considere remover essa lógica.|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
