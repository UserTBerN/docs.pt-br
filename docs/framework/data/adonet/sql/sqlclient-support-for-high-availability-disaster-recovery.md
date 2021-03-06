---
title: Suporte do SqlClient para alta disponibilidade, recuperação de desastre
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: b51c3cb1eb3c8726b7de007a1c1519eae0733392
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791617"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Suporte do SqlClient para alta disponibilidade, recuperação de desastre
Este tópico discute o suporte a SqlClient (adicionado no .NET Framework 4,5) para alta disponibilidade, recuperação de desastre-Grupos de Disponibilidade AlwaysOn.  Grupos de Disponibilidade AlwaysOn recurso foi adicionado ao SQL Server 2012. Para obter mais informações sobre Grupos de Disponibilidade AlwaysOn, consulte Manuais Online do SQL Server.  
  
 Agora você pode especificar o ouvinte do grupo de disponibilidade de um AG (grupo de disponibilidade de alta disponibilidade, recuperação de desastre) ou uma instância de cluster de failover do SQL Server 2012 na propriedade de conexão. Se um aplicativo SqlClient está conectado a um banco de dados AlwaysOn que realiza failover, a conexão original será interrompida e o aplicativo deverá abrir uma nova conexão para continuar o trabalho após o failover.  
  
 Se você não estiver se conectando a um ouvinte de grupo de disponibilidade ou SQL Server instância de cluster de failover 2012 e se vários endereços IP estiverem associados a um nome de host, o SqlClient irá iterar sequencialmente por todos os endereços IP associados à entrada DNS. Isso pode ser demorado se o primeiro endereço IP retornado pelo servidor DNS não estiver associado a nenhuma placa de interface de rede (NIC). Ao se conectar a um ouvinte de grupo de disponibilidade ou SQL Server instância de cluster de failover 2012, o SqlClient tenta estabelecer conexões com todos os endereços IP em paralelo e, se uma tentativa de conexão for bem sucedida, o driver descartará qualquer conexão pendente falhas.  
  
> [!NOTE]
> Aumentar o tempo limite de conexão e implementar lógica de novas tentativas de conexão aumenta a probabilidade de um aplicativo conectar-se a um grupo de disponibilidade. Além disso, como uma conexão pode falhar devido a um failover, você deve implementar lógica de novas tentativas de conexão, repetindo uma conexão falha até que ela se reconecte.  
  
 As propriedades de conexão a seguir foram adicionadas ao SqlClient no .NET Framework 4,5:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Você pode modificar essas palavras-chave de cadeia de caracteres de conexão por meio de programação com:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> A `MultiSubnetFailover` configuração `true` para não é necessária com .NET Framework 4.6.1 ou versões posteriores.
  
## <a name="connecting-with-multisubnetfailover"></a>Conectar-se ao MultiSubnetFailover  
 Sempre especifique `MultiSubnetFailover=True` ao se conectar a um ouvinte de grupo de disponibilidade SQL Server 2012 ou SQL Server instância de cluster de failover 2012. `MultiSubnetFailover`permite um failover mais rápido para todos os grupos de disponibilidade e a instância de cluster de failover no SQL Server 2012 e reduzirá significativamente o tempo de failover para topologias AlwaysOn de várias sub-redes. Durante um failover com várias sub-redes, o cliente tentará realizar conexões em paralelo. Durante um failover de sub-rede, ele tentará agressivamente realizar a conexão TCP.  
  
 A `MultiSubnetFailover` Propriedade Connection indica que o aplicativo está sendo implantado em um grupo de disponibilidade ou SQL Server instância de cluster de failover 2012 e que o SqlClient tentará se conectar ao banco de dados na instância de SQL Server primária ao tentar Conecte-se a todos os endereços IP. Quando `MultiSubnetFailover=True` é especificado para uma conexão, o cliente tenta novamente realizar a conexão TCP mais rapidamente do que os intervalos de retransmissão de TCP do padrão do sistema operacional. Isso permite que uma reconexão mais rápida após o failover de um Grupo de Disponibilidade AlwaysOn ou uma Instância de Cluster de Failover AlwaysOn, e é aplicável a Grupos de Disponibilidade de sub-rede único Instâncias de Cluster de Failover.  
  
 Para obter mais informações sobre palavras-chave de cadeia de caracteres de conexão no SqlClient, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Especificar `MultiSubnetFailover=True` ao conectar-se a algo diferente de um ouvinte de grupo de disponibilidade ou SQL Server instância de cluster de failover 2012 pode resultar em um impacto negativo no desempenho e não é suportado.  
  
 Use as diretrizes a seguir para se conectar a um servidor em um grupo de disponibilidade ou SQL Server instância de cluster de failover 2012:  
  
- Use a propriedade de conexão `MultiSubnetFailover` ao conectar-se a uma sub-rede única ou a várias. Isso melhora o desempenho para ambos os casos.  
  
- Para conectar-se a um grupo de disponibilidade, especifique o ouvinte de grupo de disponibilidade do grupo de disponibilidade como servidor na cadeia de caracteres de conexão.  
  
- Conectar-se a uma instância SQL Server configurada com mais de 64 endereços IP causará uma falha de conexão.  
  
- O comportamento de um aplicativo que usa `MultiSubnetFailover` a propriedade Connection não é afetado com base no tipo de autenticação: SQL Server autenticação, autenticação Kerberos ou autenticação do Windows.  
  
- Aumente o valor de `Connect Timeout` para compensar o tempo de failover e reduzir as tentativas de conexão do aplicativo.  
  
- Não há suporte para transações distribuídas.  
  
 Se o roteamento de somente leitura não estiver em vigor, conectar-se a um local de réplica secundário falhará nas seguintes situações:  
  
1. Se o local de réplica secundário não estiver configurado para aceitar conexões.  
  
2. Se um aplicativo usar `ApplicationIntent=ReadWrite` (discutido abaixo) e o local de réplica secundário estiver configurado para acesso de somente leitura.  
  
 <xref:System.Data.SqlClient.SqlDependency> não é suportado em réplicas secundárias de somente leitura.  
  
 Uma conexão falhará se a réplica primária estiver configurada para rejeitar as cargas de trabalho de somente leitura e a cadeia de caracteres da conexão contém `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Atualizando para usar vários clusters de sub-redes do espelhamento do banco de dados  
 Um erro de conexão (<xref:System.ArgumentException>) ocorrerá se as palavras-chave de conexão `MultiSubnetFailover` e `Failover Partner` estiverem presentes na cadeia de conexão, ou se `MultiSubnetFailover=True` e um protocolo diferente do TCP for usado. Um erro (<xref:System.Data.SqlClient.SqlException>) também ocorrerá se `MultiSubnetFailover` for usado e o SQL Server retornar uma resposta de parceiro de failover indicando que ele faz parte de um par de espelhamento de banco de dados.  
  
 Se você atualizar um aplicativo SqlClient que atualmente usa o espelhamento de banco de dados para um cenário de várias sub-redes, deverá remover a propriedade de conexão `Failover Partner` e substituí-la por `MultiSubnetFailover` definida como `True`, além de substituir o nome do servidor na cadeia de conexão por um ouvinte do grupo de disponibilidade. Se uma cadeia de conexão usar `Failover Partner` e `MultiSubnetFailover=True`, o driver gerará um erro. No entanto, se uma cadeia de conexão usa `Failover Partner` e `MultiSubnetFailover=False` (ou `ApplicationIntent=ReadWrite`), o aplicativo irá usar o espelhamento de banco de dados.  
  
 O driver retornará um erro se o espelhamento do banco de dados for usado no banco de dados primário na AG e se `MultiSubnetFailover=True` for usado na cadeia de conexão que se conecta a um banco de dados principal, em vez de um ouvinte de grupo de disponibilidade.  
  
## <a name="specifying-application-intent"></a>Especificando a intenção do aplicativo  
 Quando `ApplicationIntent=ReadOnly`, o cliente solicita uma carga de trabalho de leitura ao se conectar a um banco de dados habilitado para AlwaysOn. O servidor irá impor a intenção no momento da conexão e durante uma instrução de banco de dados USE, mas apenas para um banco de dados habilitado para AlwaysOn.  
  
 A palavra-chave `ApplicationIntent` não funciona com bancos de dados legados de somente leitura.  
  
 Um banco de dados pode permitir ou impedir cargas de trabalho de leitura no banco de dados AlwaysOn de destino. (Isso é feito com a `ALLOW_CONNECTIONS` cláusula `PRIMARY_ROLE` das `SECONDARY_ROLE`instruções Transact-SQL.)  
  
 A palavra-chave `ApplicationIntent` é usada para ativar o roteamento de somente leitura.  
  
## <a name="read-only-routing"></a>Roteamento de somente leitura  
 Roteamento de somente leitura é um recurso que pode garantir a disponibilidade de uma réplica de somente leitura de um banco de dados. Para habilitar o roteamento de somente leitura:  
  
1. Você deve se conectar a um ouvinte do Grupo de Disponibilidade Always On.  
  
2. A palavra-chave da cadeia de conexão `ApplicationIntent` deve ser definida como `ReadOnly`.  
  
3. O Grupo de Disponibilidade deve ser configurado pelo administrador do banco de dados para habilitar o roteamento de somente leitura.  
  
 É possível que várias conexões usando o roteamento de somente leitura serão não se conectam à mesma réplica somente leitura. Alterações na sincronização ou alteração de banco de dados na configuração de roteamento do servidor podem resultar em conexões de cliente para diferentes réplicas somente leitura. Para garantir que todas as solicitações de somente leitura se conectem à mesma réplica somente leitura, não passe um ouvinte de grupo de disponibilidade para a palavra-chave da cadeia de conexão `Data Source`. Em vez disso, especifique o nome da instância de somente leitura.  
  
 O roteamento de somente leitura pode demorar mais do que a conexão principal porque ele primeiro se conecta ao primário e, em seguida, procura o melhor secundário legível disponível. Por isso, aumente o tempo limite de logon.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Features and ADO.NET](sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
