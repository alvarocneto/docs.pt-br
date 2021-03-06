---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: cb5afb0e73ad0a07ea43f06915f4e477d7f8f985
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841547"
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<comportamento de >  
\<clientCredentials>  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Cadeia de caracteres obrigatória. Especifica o URI do emissor local.|  
|associação|Cadeia de caracteres opcional. Uma das associações fornecidas pelo sistema. Para obter uma lista, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Cadeia de caracteres opcional. Especifica uma configuração de associação encontrada no arquivo de configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica informações de identidade para o emissor local.|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalhos de endereço que são necessários para tratar corretamente o emissor local. Você pode usar o `add` palavra-chave para adicionar um cabeçalho a esta coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Especifica um token personalizado usado para autenticar um cliente a um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Ao obter um token emitido de um Security Token Service (STS), o aplicativo cliente deve ser configurado com o endereço e associação a ser usada para se comunicar com o STS. Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança, ou quando é o endereço do emissor de uma associação federado `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`, o canal do cliente Windows Communication Foundation (WCF) usa os valores especificados pelo `address`e `binding` para se comunicar com o STS a fim de obter o token emitido. Para obter mais informações sobre como configurar um emissor local, consulte [como: configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o `address`, `binding`, e `bindingConfiguration` atributos de um `localIssuer` elemento.  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Como configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Como criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
