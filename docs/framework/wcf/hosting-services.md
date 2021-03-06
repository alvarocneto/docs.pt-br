---
title: Serviços de hospedagem
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: d4fb974cdfec87606f13b5cbd83be2c86f2a1ae5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807847"
---
# <a name="hosting-services"></a>Serviços de hospedagem
Para se tornar ativa, um serviço deve ser hospedado em um ambiente de tempo de execução que cria e controla o contexto e o tempo de vida. Serviços Windows Communication Foundation (WCF) são projetados para funcionar em qualquer processo do Windows que dá suporte a código gerenciado.  
  
 O WCF fornece um modelo de programação unificado para a criação de aplicativos orientados a serviços. Este modelo de programação permanece consistente e é independente do ambiente de tempo de execução no qual o serviço é implantado. Na prática, isso significa que o código para seus serviços parece muito mesmo que a opção de hospedagem.  
  
 Esses hospedando as opções variam de execução dentro de um aplicativo de console para ambientes de servidor, como um serviço Windows em execução dentro de um processo de trabalho gerenciadas por serviços de informações da Internet (IIS) ou pelo serviço de ativação de processo para Windows (WAS). Os desenvolvedores escolham o ambiente de hospedagem que satisfaz os requisitos de implantação do serviço. Esses requisitos podem derivar da plataforma na qual o aplicativo é implantado, o transporte no qual ele deve enviar e receber mensagens, ou no tipo de reciclagem de processo e outro gerenciamento de processo necessário para garantir a disponibilidade adequada ou em alguns outros requisitos de gerenciamento ou a confiabilidade. A próxima seção fornece informações e diretrizes sobre opções de hospedagem.  
  
## <a name="hosting-options"></a>Hospedando opções  
  
#### <a name="self-hosting-in-a-managed-application"></a>Hospedagem interna em um aplicativo gerenciado  
 Serviços WCF podem ser hospedados em qualquer aplicativo gerenciado. Essa é a opção mais flexível porque ela exige a menor infra-estrutura para implantar. O código inserido para o serviço dentro do código de aplicativo gerenciado e criar e abrir uma instância do <xref:System.ServiceModel.ServiceHost> para disponibilizar o serviço. Para obter mais informações, consulte [como: hospedar um serviço WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Essa opção permite que os dois cenários comuns: serviços WCF em execução em aplicativos de console e aplicativos cliente avançados, como aqueles baseiam em Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Hospedar um serviço WCF dentro de um aplicativo de console é normalmente útil durante a fase de desenvolvimento do aplicativo. Isso os torna fácil depurar obter informações de rastreamento para descobrir o que está acontecendo no aplicativo e fácil de mover copiando-os para novos locais. Essa opção de hospedagem também torna mais fácil para aplicativos cliente avançados, como [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] e aplicativos WinForms, para se comunicar com o mundo exterior. Por exemplo, um cliente de colaboração ponto a ponto que usa [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] para sua interface de usuário e também hospeda um serviço WCF que permite que outros clientes para se conectar a ele e compartilhar informações.  
  
#### <a name="managed-windows-services"></a>Serviços do Windows gerenciado  
 Essa opção de hospedagem consiste registrando o domínio de aplicativo (AppDomain) que hospeda um serviço do WCF como um serviço gerenciado do Windows (anteriormente conhecido como serviço NT) para que o tempo de vida do processo do serviço é controlado pelo Gerenciador de controle de serviços (SCM) para Serviços do Windows. Como a opção de hospedagem interna, esse tipo de ambiente de hospedagem requer que um código de hospedagem é gravado como parte do aplicativo. O serviço é implementado como um serviço do Windows e como um serviço WCF, fazendo com que ela herde o <xref:System.ServiceProcess.ServiceBase> classe, bem como a interface de contrato de serviço de um WCF. O <xref:System.ServiceModel.ServiceHost> é criado e aberto dentro de uma substituição <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> método e fechadas dentro de uma substituição <xref:System.ServiceProcess.ServiceBase.OnStop> método. Uma classe de instalador que herda de <xref:System.Configuration.Install.Installer> também deve ser implementado para permitir que o programa seja instalado como um serviço do Windows, a ferramenta Installutil.exe. Para obter mais informações, consulte [como: hospedar um serviço WCF em um serviço do Windows gerenciado](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). O cenário habilitado pela opção de hospedagem de serviço gerenciado do Windows é que um serviço WCF de longa execução hospedado fora do IIS em um ambiente seguro não mensagem-ativada. O tempo de vida do serviço é controlado pelo sistema operacional. Essa opção de hospedagem está disponível em todas as versões do Windows.  
  
#### <a name="internet-information-services-iis"></a>Serviços de Informações da Internet (IIS)  
 O opção de hospedagem do IIS é integrado com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] e usa os recursos que oferecem essas tecnologias, como desligamento ocioso, reciclagem de processo, o monitoramento de integridade do processo e a ativação baseada em mensagem. Sobre o [!INCLUDE[wxp](../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] sistemas operacionais, isso é a solução preferida para hospedar aplicativos do serviço Web que devem ser altamente disponível e altamente escalonável. O IIS também oferece a capacidade de gerenciamento integrada que os clientes esperam de um produto de servidor corporativo. Essa opção de hospedando requer que o IIS esteja configurado corretamente, mas não requer que nenhum código de hospedagem seja escrito como parte do aplicativo. Para obter mais informações sobre como configurar o IIS de hospedagem para um serviço WCF, consulte [como: hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Observe que os serviços hospedados no IIS só podem usar o transporte HTTP. Sua implementação no IIS 5.1 introduziu algumas limitações em [!INCLUDE[wxp](../../../includes/wxp-md.md)]. A ativação baseada em mensagem fornecida para um serviço WCF pelo IIS 5.1 no [!INCLUDE[wxp](../../../includes/wxp-md.md)] bloqueia a qualquer outro serviço WCF auto-hospedado no mesmo computador que usa a porta 80 para se comunicar. Serviços WCF podem ser executados no mesmo processo de trabalho/Pool AppDomain/aplicativo como outros aplicativos quando hospedado por [!INCLUDE[iis601](../../../includes/iis601-md.md)] em [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Mas como WCF e [!INCLUDE[iis601](../../../includes/iis601-md.md)] usam a pilha HTTP de modo kernel (HTTP.sys), [!INCLUDE[iis601](../../../includes/iis601-md.md)] podem compartilhar a porta 80 com outros serviços WCF auto-hospedado em execução no mesmo computador, ao contrário do IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Serviço de Ativação de Processos do Windows (WAS)  
 O serviço de ativação de processos do Windows (WAS) é o novo mecanismo de ativação de processo para o [!INCLUDE[lserver](../../../includes/lserver-md.md)] que também está disponível em [!INCLUDE[wv](../../../includes/wv-md.md)]. Ele retém o familiar [!INCLUDE[iis601](../../../includes/iis601-md.md)] modelo de processo (pools de aplicativos e ativação de processos com base em mensagem) e hospedagem recursos (como proteção rápida contra falha, o monitoramento de integridade e reciclagem), mas ele remove a dependência no HTTP a ativação arquitetura. [!INCLUDE[iisver](../../../includes/iisver-md.md)] usa o WAS para realizar a ativação baseada em mensagem sobre HTTP. Componentes adicionais do WCF também Conecte WAS para fornecer a ativação baseada em mensagem sobre outros protocolos que dá suporte ao WCF, como pipes nomeados, TCP e MSMQ. Isso permite que aplicativos que usam protocolos de comunicação para usar os recursos do IIS, como a reciclagem de processos, rápidos não proteção e o sistema de configuração comum que só estavam disponíveis para aplicativos baseados em HTTP.  
  
 Essa opção de hospedagem requer que foi configurado corretamente, mas não é necessário gravar qualquer código de hospedagem como parte do aplicativo. Para obter mais informações sobre como configurar ESTAVA hospedando, consulte [como: hospedar um serviço WCF em WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Escolhendo um ambiente de hospedagem  
 A tabela a seguir resume alguns dos principais benefícios e cenários associados a cada uma das opções de hospedagem.  
  
|Ambiente de hospedagem|Cenários comuns|Principais benefícios e limitações|  
|-------------------------|----------------------|----------------------------------|  
|Aplicativo gerenciado ("auto-hospedado")|-Usados durante o desenvolvimento de aplicativos de console.<br />-Rich WinForm e [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplicativos cliente que acessam os serviços.|-Flexível.<br />-Fácil de implantar.<br />-Não uma solução empresarial para serviços.|  
|Serviços do Windows (anteriormente conhecido como serviços NT)|-Um serviço WCF de longa execução hospedado fora do IIS.|-Serviço tempo de vida processo controlado pelo sistema operacional, não ativado a mensagem.<br />-Suporte para todas as versões do Windows.<br />-Proteger o ambiente.|  
|IIS 5.1, [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-Um WCF em execução do serviço lado a lado com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] conteúdo na Internet usando o protocolo HTTP.|-Reciclagem do processo.<br />-Desligamento ocioso.<br />-Processo de monitoramento de integridade.<br />-Ativação baseada em mensagem.<br />-HTTP.|  
|Serviço de Ativação de Processos do Windows (WAS)|-Executando um serviço WCF sem instalar o IIS na Internet usando vários protocolos de transporte.|-IIS não é necessário.<br />-Reciclagem do processo.<br />-Desligamento ocioso.<br />-Processo de monitoramento de integridade.<br />-Ativação baseada em mensagem.<br />-Funciona com HTTP, TCP, pipes nomeados e MSMQ.|  
|IIS 7.0|-Um WCF em execução do serviço com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] conteúdo.<br />-Executando um serviço WCF na Internet usando vários protocolos de transporte.|-FOI benefícios.<br />-Integrado com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] e conteúdo do IIS.|  
  
 A escolha de um ambiente de hospedagem depende da versão do Windows na qual ele é implantado, os transportes que ele requer o envio de mensagens e o tipo de processo e reciclagem de domínio de aplicativo requer. A tabela a seguir resume os dados relacionados a esses requisitos.  
  
|Ambiente de hospedagem|Disponibilidade de plataforma|Transportes com suporte|Processo e reciclagem de AppDomain|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Aplicativos gerenciados ("auto-hospedado")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Não|  
|Serviços do Windows (anteriormente conhecido como serviços NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Não|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Sim|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Sim|  
|Serviço de Ativação de Processos do Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Sim|  
  
 É importante observar que executando um serviço ou qualquer extensão de segurança de comprometer um host não confiável. Além disso, observe que, ao abrir um <xref:System.ServiceModel.ServiceHost> em representação, um aplicativo deve garantir que o usuário não estiver conectado, por exemplo armazenando em cache o <xref:System.Security.Principal.WindowsIdentity> do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Requisitos do sistema](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [Como hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Como hospedar um serviço do WCF no WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Como hospedar um serviço WCF em um serviço Windows gerenciado](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Como hospedar um serviço do WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
