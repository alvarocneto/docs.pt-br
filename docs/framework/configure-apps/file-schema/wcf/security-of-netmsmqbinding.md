---
title: "&lt;segurança&gt; do &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 15ebbd1f0f139ef0d66ed802b990876735074485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a>&lt;segurança&gt; do &lt;netMsmqBinding&gt;
Define as configurações de segurança para uma associação de MSMQ. Especifica se o transporte ou segurança SOAP está habilitada e, em caso afirmativo, quais níveis de proteção e o modo de autenticação estão em uso.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<netMsmqBinding >  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|modo|Especifica o tipo de segurança que controla a confidencialidade, integridade e a autenticação. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Isso desabilita a segurança.<br />-Transporte: Autenticação e proteção são oferecidos pelo transporte. Isso se aplica à segurança de mensagem entre os gerenciadores de fila de dois. Não há nenhuma segurança oferecida entre o aplicativo e o Gerenciador de fila. Os aplicativos Msmq existentes são funcionalmente equivalentes com esse tipo de modo de segurança.<br />-Mensagem: Especifica a segurança do aplicativo ponta. Não há nenhuma segurança oferecida na camada de transporte. Isso é semelhante para a segurança oferecida por outras associações padrão.<br />-Ambos: Oferece segurança de transporte e de camada de mensagens SOAP. A mesma credencial é necessária em ambos os níveis.<br /><br /> O valor padrão é o transporte. Esse atributo é do tipo <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<mensagem >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|Define as configurações de segurança de mensagem SOAP. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|Define as configurações de segurança para o transporte MSMQ. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associação|O elemento de associação do [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)