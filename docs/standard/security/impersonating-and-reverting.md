---
title: Representando e revertendo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 14b01ec3ac800abd795e87b641a442df100f102b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706013"
---
# <a name="impersonating-and-reverting"></a>Representando e revertendo
Às vezes, talvez seja necessário obter um token de conta do Windows para representar uma conta do Windows. Por exemplo, seu aplicativo baseado em ASP.NET pode ter que agir em nome de vários usuários em momentos diferentes. Seu aplicativo pode aceitar um token que representa um administrador do Serviços de Informações da Internet (IIS), representar esse usuário, executar uma operação e reverter para a identidade anterior. Em seguida, ele pode aceitar um token do IIS que representa um usuário com menos direitos, executar alguma operação e reverter novamente.  
  
 Em situações em que o aplicativo deve representar uma conta do Windows que não foi anexada ao thread atual pelo IIS, você deve recuperar o token dessa conta e usá-lo para ativar a conta. Você pode fazer isso executando as seguintes tarefas:  
  
1. Recuperar um token de conta para um usuário específico fazendo uma chamada para o método **LogonUser** não gerenciado. Esse método não está na biblioteca de classes base .NET Framework, mas está localizado no **advapi32. dll**não gerenciado. O acesso a métodos em código não gerenciado é uma operação avançada e está além do escopo desta discussão. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../docs/framework/interop/index.md). Para obter mais informações sobre o método **LogonUser** e o **advapi32. dll**, consulte a documentação do Platform SDK.  
  
2. Crie uma nova instância da classe **WindowsIdentity** , passando o token. O código a seguir demonstra essa chamada, em que `hToken` representa um token do Windows.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. Comece a representação criando uma nova instância da classe <xref:System.Security.Principal.WindowsImpersonationContext> e inicializando-a com o método <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> da classe inicializada, conforme mostrado no código a seguir.  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Quando você não precisar mais representar, chame o método <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> para reverter a representação, conforme mostrado no código a seguir.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Se o código confiável já tiver anexado um objeto <xref:System.Security.Principal.WindowsPrincipal> ao thread, você poderá chamar o método de instância **Impersonate**, que não tem um token de conta. Observe que isso só é útil quando o objeto **WindowsPrincipal** no thread representa um usuário diferente daquele no qual o processo está em execução no momento. Por exemplo, você pode encontrar essa situação usando o ASP.NET com a autenticação do Windows ativada e a representação desativada. Nesse caso, o processo é executado em uma conta configurada no Serviços de Informações da Internet (IIS), enquanto a entidade atual representa o usuário do Windows que está acessando a página.  
  
 Observe que nem **Impersonate** nem **Undo** altera o objeto **principal** (<xref:System.Security.Principal.IPrincipal>) associado ao contexto de chamada atual. Em vez disso, a representação e a reversão alteram o token associado ao processo do sistema operacional atual.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
- [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)
