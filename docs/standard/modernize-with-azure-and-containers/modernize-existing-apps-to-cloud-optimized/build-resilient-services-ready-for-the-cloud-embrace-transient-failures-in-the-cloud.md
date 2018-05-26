---
title: Crie serviços resilientes prontos para a nuvem. Adotar as falhas transitórias na nuvem
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Crie serviços resilientes prontos para a nuvem. Adotar as falhas transitórias na nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 1df21d0f647b96c315686921276be3526f66bbc8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="9cf52-105">Criar serviços resilientes prontos para a nuvem: adotar falhas transitórias na nuvem</span><span class="sxs-lookup"><span data-stu-id="9cf52-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="9cf52-106">A resiliência é a capacidade de recuperar de falhas e continuar a funcionar.</span><span class="sxs-lookup"><span data-stu-id="9cf52-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="9cf52-107">Resiliência não é sobre como evitar falhas, mas aceitando o fato de que as falhas ocorrerão e, em seguida, responder a eles de maneira que evita o tempo de inatividade ou perda de dados.</span><span class="sxs-lookup"><span data-stu-id="9cf52-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="9cf52-108">A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.</span><span class="sxs-lookup"><span data-stu-id="9cf52-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="9cf52-109">O aplicativo está pronto para a nuvem quando, no mínimo, ele implementa um modelo baseado em software de resiliência, em vez de um modelo baseado em hardware.</span><span class="sxs-lookup"><span data-stu-id="9cf52-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="9cf52-110">Seu aplicativo de nuvem deve compreender as falhas parciais que certamente ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="9cf52-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="9cf52-111">O design ou parcialmente refatorar seu aplicativo para obter resiliência com falhas parciais esperadas.</span><span class="sxs-lookup"><span data-stu-id="9cf52-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="9cf52-112">Deve ser projetado para lidar com falhas parciais, como interrupções de rede transitório e nós ou VMs falhas na nuvem.</span><span class="sxs-lookup"><span data-stu-id="9cf52-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="9cf52-113">Contêineres mesmo sendo movidos para outro nó em um cluster do orchestrator podem causar falhas intermitentes de curtas dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cf52-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="9cf52-114">Tratando falha parcial</span><span class="sxs-lookup"><span data-stu-id="9cf52-114">Handling partial failure</span></span>

<span data-ttu-id="9cf52-115">Em um aplicativo baseado em nuvem, há um risco de falha parcial de sempre presente.</span><span class="sxs-lookup"><span data-stu-id="9cf52-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="9cf52-116">Por exemplo, uma instância de site único ou um contêiner pode falhar, ou ele pode estar indisponível ou não responder por um curto período.</span><span class="sxs-lookup"><span data-stu-id="9cf52-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="9cf52-117">Ou, um único servidor ou VM pode falhar.</span><span class="sxs-lookup"><span data-stu-id="9cf52-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="9cf52-118">Como os clientes e serviços são processos separados, um serviço não poderá responder de maneira oportuna a solicitação do cliente.</span><span class="sxs-lookup"><span data-stu-id="9cf52-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="9cf52-119">O serviço pode estar sobrecarregado e lenta responder às solicitações, ou ele pode não estar acessível por um curto período devido a problemas de rede.</span><span class="sxs-lookup"><span data-stu-id="9cf52-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="9cf52-120">Por exemplo, considere um aplicativo .NET monolítico que acessa um banco de dados no banco de dados do SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="9cf52-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="9cf52-121">Se o banco de dados do SQL Azure ou qualquer outro serviço de terceiros não está respondendo para um breve tempo (um banco de dados do SQL Azure pode ser movido para um nó diferente ou servidor e ficar sem resposta por alguns segundos), quando o usuário tenta realizar qualquer ação, o aplicativo pode falhar e mostrar w uma exceção ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9cf52-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="9cf52-122">Um cenário semelhante pode ocorrer em um aplicativo que consome serviços HTTP.</span><span class="sxs-lookup"><span data-stu-id="9cf52-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="9cf52-123">A rede ou o próprio serviço pode não estar disponível na nuvem durante uma falha transitória, curta.</span><span class="sxs-lookup"><span data-stu-id="9cf52-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="9cf52-124">Um aplicativo resiliente, como mostrado na Figura 4-9 deve implementar técnicas, como "repetições com retirada exponencial" para que o aplicativo tenha a oportunidade para lidar com falhas transitórias de recursos.</span><span class="sxs-lookup"><span data-stu-id="9cf52-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="9cf52-125">Você também deve usar "disjuntores" em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9cf52-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="9cf52-126">Um disjuntor interrompe um aplicativo tentar acessar um recurso quando ela é realmente uma falha de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="9cf52-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="9cf52-127">Ao usar um disjuntor, o aplicativo evita provocar uma negação de serviço para si mesmo.</span><span class="sxs-lookup"><span data-stu-id="9cf52-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![Falhas parciais tratadas pelas novas tentativas com retirada exponencial](./media/image9.png)

> <span data-ttu-id="9cf52-129">**Figura 4-9.**</span><span class="sxs-lookup"><span data-stu-id="9cf52-129">**Figure 4-9.**</span></span> <span data-ttu-id="9cf52-130">Falhas parciais tratadas pelas novas tentativas com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="9cf52-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="9cf52-131">Você pode usar essas técnicas em recursos HTTP e nos recursos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9cf52-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="9cf52-132">Na Figura 4-9, o aplicativo é baseado em uma arquitetura de camada 3, portanto, você precisa estas técnicas no nível de serviços (HTTP) e no nível da camada de dados (TCP).</span><span class="sxs-lookup"><span data-stu-id="9cf52-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="9cf52-133">Em um aplicativo monolítico que usa somente uma camada de aplicativo único além do banco de dados (não há serviços adicionais ou microservices), tratar falhas temporárias no nível de conexão do banco de dados pode ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="9cf52-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="9cf52-134">Nesse cenário, é necessária apenas uma configuração específica de conexão de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9cf52-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="9cf52-135">Ao implementar comunicações resilientes que acessam o banco de dados, dependendo da versão do .NET que você está usando, ele pode ser simples (por exemplo, [com o Entity Framework 6 ou posterior](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), é apenas uma questão de configurar o conexão de banco de dados).</span><span class="sxs-lookup"><span data-stu-id="9cf52-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), it's just a matter of configuring the database connection).</span></span> <span data-ttu-id="9cf52-136">Ou, talvez seja necessário usar as bibliotecas adicionais como o [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (para versões anteriores do .NET), ou até mesmo implementar sua própria biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9cf52-136">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="9cf52-137">Ao implementar tentativas HTTP e disjuntores, a recomendação para .NET é usar o [Polly](https://github.com/App-vNext/Polly) biblioteca, que tem como alvo o .NET Framework 4.0, .NET Framework 4.5 e .NET padrão 1.1, que inclui suporte ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9cf52-137">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="9cf52-138">Para saber como implementar estratégias para lidar com falhas parciais na nuvem, consulte as seguintes referências.</span><span class="sxs-lookup"><span data-stu-id="9cf52-138">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9cf52-139">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="9cf52-139">Additional resources</span></span>

-   <span data-ttu-id="9cf52-140">**Implementar a comunicação flexível para lidar com falhas parciais**</span><span class="sxs-lookup"><span data-stu-id="9cf52-140">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   <span data-ttu-id="9cf52-141">**Entity Framework conexão resiliência lógica e repetição (versão 6 e posterior)**</span><span class="sxs-lookup"><span data-stu-id="9cf52-141">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   <span data-ttu-id="9cf52-142">**O Transient Fault Handling Application Block**</span><span class="sxs-lookup"><span data-stu-id="9cf52-142">**The Transient Fault Handling Application Block**</span></span>

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   <span data-ttu-id="9cf52-143">**Biblioteca de Polly para comunicação de HTTP resiliente**</span><span class="sxs-lookup"><span data-stu-id="9cf52-143">**Polly library for resilient HTTP communication**</span></span>

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
<span data-ttu-id="9cf52-144">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Próximo](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="9cf52-144">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>