---
title: "Especificando comportamento de tempo de execução de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f37259a971ab20cf68776ac9889615929996ad00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-service-run-time-behavior"></a><span data-ttu-id="e1556-102">Especificando comportamento de tempo de execução de serviço</span><span class="sxs-lookup"><span data-stu-id="e1556-102">Specifying Service Run-Time Behavior</span></span>
<span data-ttu-id="e1556-103">Depois que você tiver criado um contrato de serviço ([Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)) e implementado o contrato de serviço ([implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)) você pode configurar o comportamento da operação das tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-103">Once you have designed a service contract ([Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)) and implemented your service contract ([Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)) you can configure the operation behavior of the service runtime.</span></span> <span data-ttu-id="e1556-104">Este tópico discute o serviço fornecido pelo sistema e comportamentos de operação e descreve onde encontrar mais informações para criar novos comportamentos.</span><span class="sxs-lookup"><span data-stu-id="e1556-104">This topic discusses system-provided service and operation behaviors and describes where to find more information to create new behaviors.</span></span> <span data-ttu-id="e1556-105">Enquanto alguns comportamentos são aplicados como atributos, muitos são aplicados usando um arquivo de configuração do aplicativo ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="e1556-105">While some behaviors are applied as attributes, many are applied using an application configuration file or programmatically.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e1556-106">como configurar seu aplicativo de serviço, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="e1556-106"> configuring your service application, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e1556-107">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="e1556-107">Overview</span></span>  
 <span data-ttu-id="e1556-108">O contrato define as entradas, saídas, tipos de dados e recursos de um serviço desse tipo.</span><span class="sxs-lookup"><span data-stu-id="e1556-108">The contract defines the inputs, outputs, data types, and capabilities of a service of that type.</span></span> <span data-ttu-id="e1556-109">Implementar um contrato de serviço cria uma classe que, quando configurado com uma associação em um endereço, preenche o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="e1556-109">Implementing a service contract creates a class that, when configured with a binding at an address, fulfills the contract it implements.</span></span> <span data-ttu-id="e1556-110">Contratual, associação e informações de endereço são todos conhecidos pelo cliente; sem eles, o cliente não pode fazer uso do serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-110">Contractual, binding, and address information are all known by the client; without them, the client cannot make use of the service.</span></span>  
  
 <span data-ttu-id="e1556-111">No entanto, as especificações de operação, como problemas ou gerenciamento de instâncias de threading são opacas para clientes.</span><span class="sxs-lookup"><span data-stu-id="e1556-111">However, operation specifics, such as threading issues or instance management, are opaque to clients.</span></span> <span data-ttu-id="e1556-112">Depois que você implementou o contrato de serviço, você pode configurar um grande número de características de operação usando *comportamentos*.</span><span class="sxs-lookup"><span data-stu-id="e1556-112">Once you have implemented your service contract, you can configure a large number of operation characteristics by using *behaviors*.</span></span> <span data-ttu-id="e1556-113">Comportamentos são objetos que modificam o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] definindo uma propriedade de tempo de execução ou inserindo um tipo de personalização no tempo de execução em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e1556-113">Behaviors are objects that modify the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] runtime by either setting a runtime property or by inserting a customization type into the runtime.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e1556-114">modificando o tempo de execução Criando comportamentos definidos pelo usuário, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span><span class="sxs-lookup"><span data-stu-id="e1556-114"> modifying the runtime by creating user-defined behaviors, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
 <span data-ttu-id="e1556-115">O <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> e <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> os atributos são os mais úteis comportamentos e expor solicitado o mais recursos de operação.</span><span class="sxs-lookup"><span data-stu-id="e1556-115">The <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> attributes are the most widely useful behaviors and expose the most commonly requested operation features.</span></span> <span data-ttu-id="e1556-116">Porque eles são atributos, você pode aplicá-los para a implementação de serviço ou operação.</span><span class="sxs-lookup"><span data-stu-id="e1556-116">Because they are attributes, you apply them to the service or operation implementation.</span></span> <span data-ttu-id="e1556-117">Outros comportamentos, como o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, normalmente são aplicadas usando um arquivo de configuração do aplicativo, embora você possa usá-los por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="e1556-117">Other behaviors, such as the <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, are typically applied using an application configuration file, although you can use them programmatically.</span></span>  
  
 <span data-ttu-id="e1556-118">Este tópico fornece uma visão geral de <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos, descreve os vários escopos, em que os comportamentos podem operar e fornece uma breve descrição dos muitos dos comportamentos em vários escopos que podem ser fornecidos pelo sistema útil para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="e1556-118">This topic provides an overview of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes, describes the various scopes at which behaviors can operate, and provides a quick description of many of the system-provided behaviors at the various scopes that may be of interest to [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] developers.</span></span>  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a><span data-ttu-id="e1556-119">ServiceBehaviorAttribute e OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="e1556-119">ServiceBehaviorAttribute and OperationBehaviorAttribute</span></span>  
 <span data-ttu-id="e1556-120">Os comportamentos mais importantes são o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos, que você pode usar para controlar:</span><span class="sxs-lookup"><span data-stu-id="e1556-120">The most important behaviors are the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes, which you can use to control:</span></span>  
  
-   <span data-ttu-id="e1556-121">Tempos de vida da instância</span><span class="sxs-lookup"><span data-stu-id="e1556-121">Instance lifetimes</span></span>  
  
-   <span data-ttu-id="e1556-122">Suporte a simultaneidade e sincronização</span><span class="sxs-lookup"><span data-stu-id="e1556-122">Concurrency and synchronization support</span></span>  
  
-   <span data-ttu-id="e1556-123">Comportamento de configuração</span><span class="sxs-lookup"><span data-stu-id="e1556-123">Configuration behavior</span></span>  
  
-   <span data-ttu-id="e1556-124">Comportamento de transação</span><span class="sxs-lookup"><span data-stu-id="e1556-124">Transaction behavior</span></span>  
  
-   <span data-ttu-id="e1556-125">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="e1556-125">Serialization behavior</span></span>  
  
-   <span data-ttu-id="e1556-126">Transformação de metadados</span><span class="sxs-lookup"><span data-stu-id="e1556-126">Metadata transformation</span></span>  
  
-   <span data-ttu-id="e1556-127">Duração da sessão</span><span class="sxs-lookup"><span data-stu-id="e1556-127">Session lifetime</span></span>  
  
-   <span data-ttu-id="e1556-128">Filtragem de endereço e o processamento de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="e1556-128">Address filtering and header processing</span></span>  
  
-   <span data-ttu-id="e1556-129">Representação</span><span class="sxs-lookup"><span data-stu-id="e1556-129">Impersonation</span></span>  
  
-   <span data-ttu-id="e1556-130">Para usar esses atributos, marque a implementação de serviço ou a operação com o atributo apropriado para esse escopo e definir as propriedades.</span><span class="sxs-lookup"><span data-stu-id="e1556-130">To use these attributes, mark the service or operation implementation with the attribute appropriate to that scope and set the properties.</span></span> <span data-ttu-id="e1556-131">Por exemplo, o exemplo de código a seguir mostra uma implementação de operação que usa o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> propriedade para exigir que os chamadores dessa operação suporte à representação.</span><span class="sxs-lookup"><span data-stu-id="e1556-131">For example, the following code example shows an operation implementation that uses the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> property to require that callers of this operation support impersonation.</span></span>  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 <span data-ttu-id="e1556-132">Muitas das propriedades requerem suporte adicional da associação.</span><span class="sxs-lookup"><span data-stu-id="e1556-132">Many of the properties require additional support from the binding.</span></span> <span data-ttu-id="e1556-133">Por exemplo, uma operação que requer uma transação do cliente deve ser configurada para usar uma associação que dá suporte a transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="e1556-133">For example, an operation that requires a transaction from the client must be configured to use a binding that supports flowed transactions.</span></span>  
  
### <a name="well-known-singleton-services"></a><span data-ttu-id="e1556-134">Serviços de Singleton conhecido</span><span class="sxs-lookup"><span data-stu-id="e1556-134">Well-Known Singleton Services</span></span>  
 <span data-ttu-id="e1556-135">Você pode usar o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos para controlar determinados tempos de vida, ambos os <xref:System.ServiceModel.InstanceContext> e dos objetos de serviço que implementam as operações.</span><span class="sxs-lookup"><span data-stu-id="e1556-135">You can use the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control certain lifetimes, both of the <xref:System.ServiceModel.InstanceContext> and of the service objects that implement the operations.</span></span>  
  
 <span data-ttu-id="e1556-136">Por exemplo, o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade controla com que frequência o <xref:System.ServiceModel.InstanceContext> é liberado e o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> propriedades que controlam quando o objeto de serviço é liberado.</span><span class="sxs-lookup"><span data-stu-id="e1556-136">For example, the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> property controls how often the <xref:System.ServiceModel.InstanceContext> is released, and the <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> properties control when the service object is released.</span></span>  
  
 <span data-ttu-id="e1556-137">No entanto, também pode criar um objeto de serviço por conta própria e crie o host de serviço usando o objeto.</span><span class="sxs-lookup"><span data-stu-id="e1556-137">However, you can also create a service object yourself and create the service host using that object.</span></span> <span data-ttu-id="e1556-138">Para fazer isso, você também deve definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.InstanceContextMode.Single> ou uma exceção é lançada quando o host de serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="e1556-138">To do so, you must also set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.InstanceContextMode.Single> or an exception is thrown when the service host is opened.</span></span>  
  
 <span data-ttu-id="e1556-139">Use o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> construtor para criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-139">Use the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> constructor to create such a service.</span></span> <span data-ttu-id="e1556-140">Ele fornece uma alternativa à implementação de uma <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> quando você deseja fornecer uma instância de objeto específico para uso por um serviço de singleton.</span><span class="sxs-lookup"><span data-stu-id="e1556-140">It provides an alternative to implementing a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> when you wish to provide a specific object instance for use by a singleton service.</span></span> <span data-ttu-id="e1556-141">Você pode usar essa sobrecarga ao seu tipo de implementação de serviço é difícil construir (por exemplo, se ele não implementa um construtor público padrão que não tem parâmetros).</span><span class="sxs-lookup"><span data-stu-id="e1556-141">You can use this overload when your service implementation type is difficult to construct (for example, if it does not implement a default public constructor that has no parameters).</span></span>  
  
 <span data-ttu-id="e1556-142">Observe que quando um objeto é fornecido para esse construtor, alguns recursos relacionados a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] instância trabalho comportamento diferente.</span><span class="sxs-lookup"><span data-stu-id="e1556-142">Note that when an object is provided to this constructor, some features related to the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] instancing behavior work differently.</span></span> <span data-ttu-id="e1556-143">Por exemplo, chamar <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> não tem nenhum efeito quando uma instância de objeto conhecido é fornecida.</span><span class="sxs-lookup"><span data-stu-id="e1556-143">For example, calling <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> has no effect when a well-known object instance is provided.</span></span> <span data-ttu-id="e1556-144">Da mesma forma, qualquer outro mecanismo de versão da instância é ignorado.</span><span class="sxs-lookup"><span data-stu-id="e1556-144">Similarly, any other instance release mechanism is ignored.</span></span> <span data-ttu-id="e1556-145">O <xref:System.ServiceModel.ServiceHost> classe sempre se comporta como se o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> para todas as operações.</span><span class="sxs-lookup"><span data-stu-id="e1556-145">The <xref:System.ServiceModel.ServiceHost> class always behaves as if the <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> property is set to <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> for all operations.</span></span>  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a><span data-ttu-id="e1556-146">Outro serviço, ponto de extremidade, contrato e comportamentos de operação</span><span class="sxs-lookup"><span data-stu-id="e1556-146">Other Service, Endpoint, Contract, and Operation Behaviors</span></span>  
 <span data-ttu-id="e1556-147">Comportamentos de serviço, como o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo, operar em todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-147">Service behaviors, such as the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute, operate across an entire service.</span></span> <span data-ttu-id="e1556-148">Por exemplo, se você definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> você deve tratar problemas de sincronização de thread dentro de cada operação nesse serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-148">For example, if you set the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> you must handle thread synchronization issues inside each operation in that service yourself.</span></span> <span data-ttu-id="e1556-149">Comportamentos de ponto de extremidade operam em um ponto de extremidade; muitos dos comportamentos de ponto de extremidade fornecido pelo sistema são para a funcionalidade de cliente.</span><span class="sxs-lookup"><span data-stu-id="e1556-149">Endpoint behaviors operate across an endpoint; many of the system-provided endpoint behaviors are for client functionality.</span></span> <span data-ttu-id="e1556-150">Comportamentos de contrato operam no nível do contrato e comportamentos de operação modificar a entrega de operação.</span><span class="sxs-lookup"><span data-stu-id="e1556-150">Contract behaviors operate at the contract level, and operation behaviors modify operation delivery.</span></span>  
  
 <span data-ttu-id="e1556-151">Muitos desses comportamentos são implementados em atributos e fazer utilizá-las como faz o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos — por aplicá-las para a implementação de classe ou operação de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="e1556-151">Many of these behaviors are implemented on attributes, and you make use of them as you do the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes—by applying them to the appropriate service class or operation implementation.</span></span> <span data-ttu-id="e1556-152">Outros comportamentos, como o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior> objetos, são normalmente aplicadas usando um arquivo de configuração do aplicativo, embora também possa ser usados por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="e1556-152">Other behaviors, such as the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> or <xref:System.ServiceModel.Description.ServiceDebugBehavior> objects, are typically applied using an application configuration file, although they can also be used programmatically.</span></span>  
  
 <span data-ttu-id="e1556-153">Por exemplo, a publicação de metadados é configurada usando o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objeto.</span><span class="sxs-lookup"><span data-stu-id="e1556-153">For example, the publication of metadata is configured by using the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object.</span></span> <span data-ttu-id="e1556-154">O seguinte arquivo de configuração do aplicativo mostra o uso mais comum.</span><span class="sxs-lookup"><span data-stu-id="e1556-154">The following application configuration file shows the most common usage.</span></span>  
  
 [!code-csharp[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.cs#1)]  
  
 <span data-ttu-id="e1556-155">As seções a seguir descrevem a muitos dos comportamentos fornecido pelo sistema mais úteis que você pode usar para modificar a entrega de tempo de execução do serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="e1556-155">The following sections describe many of the most useful system-provided behaviors that you can use to modify the runtime delivery of your service or client.</span></span> <span data-ttu-id="e1556-156">Consulte o tópico de referência para determinar como usar cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="e1556-156">See the reference topic to determine how to use each one.</span></span>  
  
### <a name="service-behaviors"></a><span data-ttu-id="e1556-157">Comportamentos de serviço</span><span class="sxs-lookup"><span data-stu-id="e1556-157">Service Behaviors</span></span>  
 <span data-ttu-id="e1556-158">Os seguintes comportamentos operam nos serviços.</span><span class="sxs-lookup"><span data-stu-id="e1556-158">The following behaviors operate on services.</span></span>  
  
-   <span data-ttu-id="e1556-159"><xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e1556-159"><xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span></span> <span data-ttu-id="e1556-160">Aplicado a um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço para indicar se esse serviço pode ser executado [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] modo de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e1556-160">Applied to a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to indicate whether that service can be run in [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Compatibility Mode.</span></span>  
  
-   <span data-ttu-id="e1556-161"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-161"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span> <span data-ttu-id="e1556-162">Controla como o serviço autoriza declarações de cliente.</span><span class="sxs-lookup"><span data-stu-id="e1556-162">Controls how the service authorizes client claims.</span></span>  
  
-   <span data-ttu-id="e1556-163"><xref:System.ServiceModel.Description.ServiceCredentials>.</span><span class="sxs-lookup"><span data-stu-id="e1556-163"><xref:System.ServiceModel.Description.ServiceCredentials>.</span></span> <span data-ttu-id="e1556-164">Configura uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-164">Configures a service credential.</span></span> <span data-ttu-id="e1556-165">Use esta classe para especificar a credencial para o serviço, como um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="e1556-165">Use this class to specify the credential for the service, such as an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="e1556-166"><xref:System.ServiceModel.Description.ServiceDebugBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-166"><xref:System.ServiceModel.Description.ServiceDebugBehavior>.</span></span> <span data-ttu-id="e1556-167">Habilita a depuração e ajudar a recursos de informações para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-167">Enables debugging and Help information features for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="e1556-168"><xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-168"><xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span> <span data-ttu-id="e1556-169">Controla a publicação de metadados de serviço e informações associadas.</span><span class="sxs-lookup"><span data-stu-id="e1556-169">Controls the publication of service metadata and associated information.</span></span>  
  
-   <span data-ttu-id="e1556-170"><xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-170"><xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>.</span></span> <span data-ttu-id="e1556-171">Especifica o comportamento de auditoria de eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="e1556-171">Specifies the audit behavior of security events.</span></span>  
  
-   <span data-ttu-id="e1556-172"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-172"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior>.</span></span> <span data-ttu-id="e1556-173">Define as configurações de taxa de transferência de tempo de execução que permitem ajustar o desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-173">Configures run-time throughput settings that enable you to tune service performance.</span></span>  
  
### <a name="endpoint-behaviors"></a><span data-ttu-id="e1556-174">Comportamentos de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="e1556-174">Endpoint Behaviors</span></span>  
 <span data-ttu-id="e1556-175">Os seguintes comportamentos operam nos pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e1556-175">The following behaviors operate on endpoints.</span></span> <span data-ttu-id="e1556-176">Muitos desses comportamentos são usados em aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="e1556-176">Many of these behaviors are used in client applications.</span></span>  
  
-   <span data-ttu-id="e1556-177"><xref:System.ServiceModel.CallbackBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e1556-177"><xref:System.ServiceModel.CallbackBehaviorAttribute>.</span></span> <span data-ttu-id="e1556-178">Configura uma implementação de serviço de retorno de chamada em um aplicativo cliente duplex.</span><span class="sxs-lookup"><span data-stu-id="e1556-178">Configures a callback service implementation in a duplex client application.</span></span>  
  
-   <span data-ttu-id="e1556-179"><xref:System.ServiceModel.Description.CallbackDebugBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-179"><xref:System.ServiceModel.Description.CallbackDebugBehavior>.</span></span> <span data-ttu-id="e1556-180">Habilita a depuração de serviço para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e1556-180">Enables service debugging for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] callback object.</span></span>  
  
-   <span data-ttu-id="e1556-181"><xref:System.ServiceModel.Description.ClientCredentials>.</span><span class="sxs-lookup"><span data-stu-id="e1556-181"><xref:System.ServiceModel.Description.ClientCredentials>.</span></span> <span data-ttu-id="e1556-182">Permite ao usuário configurar as credenciais de cliente e de serviço, bem como configurações de autenticação de credenciais para uso no cliente de serviço.</span><span class="sxs-lookup"><span data-stu-id="e1556-182">Allows the user to configure client and service credentials as well as service credential authentication settings for use on the client.</span></span>  
  
-   <span data-ttu-id="e1556-183"><xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-183"><xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span> <span data-ttu-id="e1556-184">Usado por clientes para especificar o identificador de URI (Uniform Resource) para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="e1556-184">Used by clients to specify the Uniform Resource Identifier (URI) for which the transport channel should be created.</span></span>  
  
-   <span data-ttu-id="e1556-185"><xref:System.ServiceModel.Description.MustUnderstandBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-185"><xref:System.ServiceModel.Description.MustUnderstandBehavior>.</span></span> <span data-ttu-id="e1556-186">Instrui o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para desabilitar o `MustUnderstand` de processamento.</span><span class="sxs-lookup"><span data-stu-id="e1556-186">Instructs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to disable the `MustUnderstand` processing.</span></span>  
  
-   <span data-ttu-id="e1556-187"><xref:System.ServiceModel.Description.SynchronousReceiveBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-187"><xref:System.ServiceModel.Description.SynchronousReceiveBehavior>.</span></span> <span data-ttu-id="e1556-188">Instrui o tempo de execução para usar um síncrono receber o processo de canais.</span><span class="sxs-lookup"><span data-stu-id="e1556-188">Instructs the runtime to use a synchronous receive process for channels.</span></span>  
  
-   <span data-ttu-id="e1556-189"><xref:System.ServiceModel.Description.TransactedBatchingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-189"><xref:System.ServiceModel.Description.TransactedBatchingBehavior>.</span></span> <span data-ttu-id="e1556-190">Otimiza as operações de recebimento para os transportes que recebe suporte transacional.</span><span class="sxs-lookup"><span data-stu-id="e1556-190">Optimizes the receive operations for transports that support transactional receives.</span></span>  
  
### <a name="contract-behaviors"></a><span data-ttu-id="e1556-191">Comportamentos de contrato</span><span class="sxs-lookup"><span data-stu-id="e1556-191">Contract Behaviors</span></span>  
 <span data-ttu-id="e1556-192"><xref:System.ServiceModel.DeliveryRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e1556-192"><xref:System.ServiceModel.DeliveryRequirementsAttribute>.</span></span> <span data-ttu-id="e1556-193">Especifica os requisitos de recurso associações devem fornecer para a implementação de serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="e1556-193">Specifies the feature requirements that bindings must provide to the service or client implementation.</span></span>  
  
### <a name="operation-behaviors"></a><span data-ttu-id="e1556-194">Comportamentos de operação</span><span class="sxs-lookup"><span data-stu-id="e1556-194">Operation Behaviors</span></span>  
 <span data-ttu-id="e1556-195">Os seguintes comportamentos de operação especificar controles de serialização e a transação para operações.</span><span class="sxs-lookup"><span data-stu-id="e1556-195">The following operation behaviors specify serialization and transaction controls for operations.</span></span>  
  
-   <span data-ttu-id="e1556-196"><xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-196"><xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span> <span data-ttu-id="e1556-197">Representa o comportamento de tempo de execução de <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1556-197">Represents the run-time behavior of the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="e1556-198"><xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e1556-198"><xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>.</span></span> <span data-ttu-id="e1556-199">Controla o comportamento de tempo de execução de `XmlSerializer` e o associa a uma operação.</span><span class="sxs-lookup"><span data-stu-id="e1556-199">Controls run-time behavior of the `XmlSerializer` and associates it with an operation.</span></span>  
  
-   <span data-ttu-id="e1556-200"><xref:System.ServiceModel.TransactionFlowAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e1556-200"><xref:System.ServiceModel.TransactionFlowAttribute>.</span></span> <span data-ttu-id="e1556-201">Especifica o nível no qual uma operação de serviço aceita um cabeçalho de transação.</span><span class="sxs-lookup"><span data-stu-id="e1556-201">Specifies the level in which a service operation accepts a transaction header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1556-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1556-202">See Also</span></span>  
 <span data-ttu-id="e1556-203">[Configuring Services](../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="e1556-203">[Configuring Services](../../../docs/framework/wcf/configuring-services.md)</span></span>  
 [<span data-ttu-id="e1556-204">Como: controlar instanciação de serviço</span><span class="sxs-lookup"><span data-stu-id="e1556-204">How to: Control Service Instancing</span></span>](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)