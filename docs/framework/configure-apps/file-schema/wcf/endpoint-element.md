---
title: elemento de &lt;ponto de extremidade&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 937819fabc50d4a0a43c6a3168e6d8a77bf4ceca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltendpointgt-element"></a><span data-ttu-id="df9a7-102">elemento de &lt;ponto de extremidade&gt;</span><span class="sxs-lookup"><span data-stu-id="df9a7-102">&lt;endpoint&gt; element</span></span>
<span data-ttu-id="df9a7-103">Especifica a associação, contrato e propriedades de endereço de um ponto de extremidade de serviço, que é usado para expor serviços.</span><span class="sxs-lookup"><span data-stu-id="df9a7-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="df9a7-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="df9a7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="df9a7-105">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="df9a7-105">\<service></span></span>  
<span data-ttu-id="df9a7-106">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="df9a7-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df9a7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df9a7-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df9a7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df9a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="df9a7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df9a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df9a7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="df9a7-110">Attributes</span></span>  
  
|<span data-ttu-id="df9a7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="df9a7-111">Attribute</span></span>|<span data-ttu-id="df9a7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="df9a7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df9a7-113">endereço</span><span class="sxs-lookup"><span data-stu-id="df9a7-113">address</span></span>|<span data-ttu-id="df9a7-114">Uma cadeia de caracteres que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="df9a7-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="df9a7-115">O endereço pode ser especificado como um endereço absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="df9a7-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="df9a7-116">Se for fornecido um endereço relativo, o host deve fornecer um endereço base apropriado para o esquema de transporte usado na associação.</span><span class="sxs-lookup"><span data-stu-id="df9a7-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="df9a7-117">Se um endereço não estiver configurado, o endereço base é considerado o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="df9a7-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="df9a7-118">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="df9a7-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="df9a7-119">behaviorConfiguration</span></span>|<span data-ttu-id="df9a7-120">Uma cadeia de caracteres que contém o nome do comportamento a ser usado no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="df9a7-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="df9a7-121">associação</span><span class="sxs-lookup"><span data-stu-id="df9a7-121">binding</span></span>|<span data-ttu-id="df9a7-122">Necessário um atributo de cadeia de caracteres que especifica o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="df9a7-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="df9a7-123">O tipo deve ter uma seção de configuração registrado para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="df9a7-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="df9a7-124">O tipo é registrado por nome de seção, em vez do nome do tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="df9a7-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="df9a7-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="df9a7-125">bindingConfiguration</span></span>|<span data-ttu-id="df9a7-126">Uma cadeia de caracteres que especifica o nome de associação da associação a ser usado quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="df9a7-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="df9a7-127">O nome da associação deve estar no escopo no ponto de que extremidade é definida.</span><span class="sxs-lookup"><span data-stu-id="df9a7-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="df9a7-128">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="df9a7-129">Este atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="df9a7-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="df9a7-130">Defina esse atributo, se você está tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="df9a7-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="df9a7-131">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="df9a7-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="df9a7-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="df9a7-132">bindingName</span></span>|<span data-ttu-id="df9a7-133">Uma cadeia de caracteres que especifica o nome qualificado exclusivo da associação para exportação de definição através de WSDL.</span><span class="sxs-lookup"><span data-stu-id="df9a7-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="df9a7-134">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="df9a7-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="df9a7-135">bindingNamespace</span></span>|<span data-ttu-id="df9a7-136">Exportar uma cadeia de caracteres que especifica o nome qualificado do namespace da associação de definição através de WSDL.</span><span class="sxs-lookup"><span data-stu-id="df9a7-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="df9a7-137">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="df9a7-138">contrato</span><span class="sxs-lookup"><span data-stu-id="df9a7-138">contract</span></span>|<span data-ttu-id="df9a7-139">Uma cadeia de caracteres que indica qual contrato esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="df9a7-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="df9a7-140">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="df9a7-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="df9a7-141">Se uma implementação de serviço implementa um tipo de contrato único, essa propriedade pode ser omitida.</span><span class="sxs-lookup"><span data-stu-id="df9a7-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="df9a7-142">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="df9a7-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="df9a7-143">endpointConfiguration</span></span>|<span data-ttu-id="df9a7-144">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, o que faz referência às informações adicionais de configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="df9a7-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="df9a7-145">O mesmo nome deve ser definido na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="df9a7-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="df9a7-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="df9a7-146">isSystemEndpoint</span></span>|<span data-ttu-id="df9a7-147">Um valor booleano que especifica se um ponto de extremidade é um ponto de extremidade de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="df9a7-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="df9a7-148">tipo</span><span class="sxs-lookup"><span data-stu-id="df9a7-148">kind</span></span>|<span data-ttu-id="df9a7-149">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="df9a7-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="df9a7-150">O tipo deve ser registrado no `<extensions>` seção ou em Machine. config. Se nada for especificado, um ponto de extremidade de serviço comum é criado.</span><span class="sxs-lookup"><span data-stu-id="df9a7-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="df9a7-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="df9a7-151">listenUriMode</span></span>|<span data-ttu-id="df9a7-152">Especifica como o transporte trata o `ListenUri` fornecido para o serviço de escuta.</span><span class="sxs-lookup"><span data-stu-id="df9a7-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="df9a7-153">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="df9a7-153">Valid values are</span></span><br /><br /> <span data-ttu-id="df9a7-154">-Explícita</span><span class="sxs-lookup"><span data-stu-id="df9a7-154">-   Explicit</span></span><br /><span data-ttu-id="df9a7-155">-Exclusivo</span><span class="sxs-lookup"><span data-stu-id="df9a7-155">-   Unique</span></span><br /><br /> <span data-ttu-id="df9a7-156">O valor padrão é Explicit.</span><span class="sxs-lookup"><span data-stu-id="df9a7-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="df9a7-157">ListenUri</span><span class="sxs-lookup"><span data-stu-id="df9a7-157">listenUri</span></span>|<span data-ttu-id="df9a7-158">Uma cadeia de caracteres que especifica o URI no qual o ponto de extremidade de serviço escuta.</span><span class="sxs-lookup"><span data-stu-id="df9a7-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="df9a7-159">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="df9a7-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="df9a7-160">name</span><span class="sxs-lookup"><span data-stu-id="df9a7-160">name</span></span>|<span data-ttu-id="df9a7-161">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="df9a7-161">Optional attribute.</span></span> <span data-ttu-id="df9a7-162">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="df9a7-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="df9a7-163">O valor padrão é a concatenação do nome de associação e o nome de descrição do contrato.</span><span class="sxs-lookup"><span data-stu-id="df9a7-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="df9a7-164">Serviços podem ter vários pontos de extremidade, portanto o ponto de extremidade `name` atributo é diferente do nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="df9a7-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df9a7-165">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df9a7-165">Child Elements</span></span>  
  
|<span data-ttu-id="df9a7-166">Elemento</span><span class="sxs-lookup"><span data-stu-id="df9a7-166">Element</span></span>|<span data-ttu-id="df9a7-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="df9a7-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df9a7-168">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="df9a7-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="df9a7-169">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="df9a7-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="df9a7-170">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="df9a7-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="df9a7-171">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="df9a7-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df9a7-172">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df9a7-172">Parent Elements</span></span>  
  
|<span data-ttu-id="df9a7-173">Elemento</span><span class="sxs-lookup"><span data-stu-id="df9a7-173">Element</span></span>|<span data-ttu-id="df9a7-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="df9a7-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df9a7-175">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="df9a7-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="df9a7-176">Uma seção de configuração que define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="df9a7-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df9a7-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df9a7-177">Example</span></span>  
 <span data-ttu-id="df9a7-178">Este é um exemplo de uma configuração de ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="df9a7-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df9a7-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df9a7-179">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [<span data-ttu-id="df9a7-180">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="df9a7-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="df9a7-181">Como: criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="df9a7-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)