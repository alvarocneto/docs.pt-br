---
title: '&lt;segurança&gt; de &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: 1d7ffaf72e34b700f4702b2e531afbf7e842de09
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844560"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a>&lt;segurança&gt; de &lt;netPeerBinding&gt;
Define as configurações de segurança de [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.  
  
 \<system.ServiceModel>  
\<associações >  
\<netPeerBinding>  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|modo|Opcional. Especifica o tipo de segurança usado por pares configurados com essa associação. O valor padrão é `Message`. Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>modo de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Mensagem|Segurança SOAP fornece autenticação, integridade e confidencialidade.|  
|Nenhum|A segurança é desabilitada.|  
|Transporte|A proteção é fornecida usando HTTPS.|  
|TransportWithMessageCredential|HTTPS fornece autenticação e confidencialidade. As mensagens SOAP fornecem tipos de credencial avançados.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|Define o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Segurança pode ser qualquer um dos específicos de mensagem ou de transporte.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Selecionando um tipo de credencial](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
