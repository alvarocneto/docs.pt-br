---
title: E aplicativos de nuvem nativo?
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | E aplicativos de nuvem nativo?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0e880689001ece2b770811cfbe3fea43aa425b32
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="what-about-cloud-native-applications"></a><span data-ttu-id="a54b3-103">E aplicativos de nuvem nativo?</span><span class="sxs-lookup"><span data-stu-id="a54b3-103">What about Cloud-Native applications?</span></span>

<span data-ttu-id="a54b3-104">Embora [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos não são o principal foco deste guia, é útil para compreender desse nível de maturidade modernização e distingui-lo de aplicativos otimizada para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="a54b3-104">Although [Cloud-Native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) applications are not the main focus of this guide, it's helpful to have an understanding of this modernization maturity level, and to distinguish it from Cloud-Optimized applications.</span></span>

<span data-ttu-id="a54b3-105">Figura 4-3 posiciona aplicativos de nuvem nativo nos níveis de maturidade modernização de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a54b3-105">Figure 4-3 positions Cloud-Native apps in the application modernization maturity levels:</span></span>

![Aplicativos de nuvem nativo de posicionamento](./media/image3.png)

> <span data-ttu-id="a54b3-107">**Figura 4-3.**</span><span class="sxs-lookup"><span data-stu-id="a54b3-107">**Figure 4-3.**</span></span> <span data-ttu-id="a54b3-108">Aplicativos de nuvem nativo de posicionamento</span><span class="sxs-lookup"><span data-stu-id="a54b3-108">Positioning Cloud-Native applications</span></span>

<span data-ttu-id="a54b3-109">O nível de maturidade modernização nativo nuvem normalmente requer investimentos de desenvolvimento de novo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-109">The Cloud-Native modernization maturity level usually requires new development investments.</span></span> <span data-ttu-id="a54b3-110">Mover para o nível de nuvem nativo normalmente é orientada por empresas que precisam modernizar aplicativos tanto quanto possíveis melhorar drasticamente escalas em aplicativos grandes criando subsistemas autônomos (microservices) que podem ser implantados e independentemente de outras áreas do aplicativo enquanto reduz os custos em agilidade longo prazo e aumento de evolução das partes do aplicativo esses autônomos que fornecem significativa competir vantagens.</span><span class="sxs-lookup"><span data-stu-id="a54b3-110">Moving to the Cloud- Native level typically is driven by business need to modernize applications as much as possible to drastically improve scale in large applications by creating autonomous subsystems (microservices) that can be deployed and scale independently from other areas of the application while lowering costs in the long term and increase evolution agility of those autonomous app’s parts that provide significant compete advantages.</span></span> 

<span data-ttu-id="a54b3-111">Principais pilares de [nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplicativos são baseados em abordagens de arquitetura microservices, que podem evoluir com agilidade e dimensionar aos limites que seriam difíceis de uma arquitetura monolítica implantada para um ambiente de nuvem ou local.</span><span class="sxs-lookup"><span data-stu-id="a54b3-111">The main pillars of [Cloud-Native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) applications are based on microservices architecture approaches, which can evolve with agility and scale to limits that would be difficult to achieve in a monolithic architecture deployed to either on-premises or cloud environment.</span></span>

<span data-ttu-id="a54b3-112">Figura 4-4 mostra as principais características do modelo de nuvem nativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-112">Figure 4-4 shows the main characteristics of the Cloud-Native model.</span></span>  

> ![Características de nuvem nativo são Microservices, contêineres, nuvem resilientes, orchestrators e serverles](./media/image4.png)
>
> <span data-ttu-id="a54b3-114">**Figura 4-4.**</span><span class="sxs-lookup"><span data-stu-id="a54b3-114">**Figure 4-4.**</span></span> <span data-ttu-id="a54b3-115">Características de nuvem nativo</span><span class="sxs-lookup"><span data-stu-id="a54b3-115">Cloud-Native characteristics</span></span>

<span data-ttu-id="a54b3-116">Além disso, você pode estender aplicativos web modernos básico e nativo de nuvem adicionando outros serviços, como inteligência artificial (AI), o aprendizado de máquina (ML) e IoT.</span><span class="sxs-lookup"><span data-stu-id="a54b3-116">In addition, you can extend basic modern web apps and cloud-native apps by adding other services, like artificial intelligence (AI), machine learning (ML), and IoT.</span></span> <span data-ttu-id="a54b3-117">Você pode usar qualquer um desses serviços para estender uma das abordagens possíveis otimizada para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="a54b3-117">You might use any of these services to extend any of the possible Cloud-Optimized approaches.</span></span>

<span data-ttu-id="a54b3-118">A diferença fundamental em aplicativos no nível de nuvem nativo está na arquitetura do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-118">The fundamental difference in applications at the Cloud-Native level is in the application architecture.</span></span> <span data-ttu-id="a54b3-119">[Nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos são, por definição, os aplicativos que se baseiam no microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-119">[Cloud-native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) applications are, by definition, apps that are based on microservices.</span></span> <span data-ttu-id="a54b3-120">Aplicativos de nuvem nativo exigem arquiteturas especiais, tecnologias e plataformas, em comparação comparadas um aplicativo web monolítico ou tradicionais de aplicativos de N camadas.</span><span class="sxs-lookup"><span data-stu-id="a54b3-120">Cloud-native apps require special architectures, technologies, and platforms, compared to a monolithic web application or traditional N-Tier application.</span></span>

## <a name="cloud-native-applications-details"></a><span data-ttu-id="a54b3-121">Detalhes de aplicativos de nuvem nativo</span><span class="sxs-lookup"><span data-stu-id="a54b3-121">Cloud-native applications details</span></span>

<span data-ttu-id="a54b3-122">[Nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) é um estado mais avançado ou mais maduro para aplicativos grandes e de missão crítica.</span><span class="sxs-lookup"><span data-stu-id="a54b3-122">[Cloud-Native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) is a more advanced or mature state for large and mission-critical applications.</span></span> <span data-ttu-id="a54b3-123">Aplicativos de nuvem nativo geralmente requerem a arquitetura e design criado do zero, em vez de por modernizar aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="a54b3-123">Cloud-Native applications usually require architecture and design that are created from scratch instead of by modernizing existing applications.</span></span> <span data-ttu-id="a54b3-124">A principal diferença entre um aplicativo nativo de nuvem e um aplicativo web com otimização de nuvem mais simples é a recomendação para usar microservices arquiteturas em uma abordagem de nuvem nativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-124">The key difference between a Cloud-Native application and a simpler Cloud-Optimized web app is the recommendation to use microservices architectures in a cloud-native approach.</span></span> <span data-ttu-id="a54b3-125">Otimização de nuvem aplicativos também podem ser aplicativos web monolítico ou aplicativos de N camadas.</span><span class="sxs-lookup"><span data-stu-id="a54b3-125">Cloud-Optimized apps can also be monolithic web apps or N-Tier apps.</span></span>

<span data-ttu-id="a54b3-126">O [aplicativo doze Factor](https://12factor.net/) (uma coleção de padrões que estão intimamente relacionados abordagens microservices) também é considerada um requisito para [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) arquiteturas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-126">The [Twelve-Factor App](https://12factor.net/) (a collection of patterns that are closely related to microservices approaches) is also considered a requirement for [cloud-native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) application architectures.</span></span>

<span data-ttu-id="a54b3-127">O [Foundation de computação nativo de nuvem (CNCF)](https://www.cncf.io/) é um Promotores primário dos princípios de nuvem nativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-127">The [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) is a primary promoter of cloud-native principles.</span></span> <span data-ttu-id="a54b3-128">A Microsoft tem um [membro o CNCF](https://azure.microsoft.com/blog/announcing-cncf/).</span><span class="sxs-lookup"><span data-stu-id="a54b3-128">Microsoft is a [member of the CNCF](https://azure.microsoft.com/blog/announcing-cncf/).</span></span>

<span data-ttu-id="a54b3-129">Para um exemplo de definição e para obter mais informações sobre as características dos aplicativos de nuvem nativo, consulte o artigo Gartner [como projetar e criar aplicativos de nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications).</span><span class="sxs-lookup"><span data-stu-id="a54b3-129">For a sample definition and for more information about the characteristics of cloud-native applications, see the Gartner article [How to architect and design cloud-native applications](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications).</span></span> <span data-ttu-id="a54b3-130">Para obter orientações específicas da Microsoft sobre como implementar um aplicativo nativo de nuvem, consulte [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook).</span><span class="sxs-lookup"><span data-stu-id="a54b3-130">For specific guidance from Microsoft about how to implement a cloud-native application, see [.NET microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook).</span></span>

<span data-ttu-id="a54b3-131">O fator mais importante a considerar se você migrar um aplicativo completo para o [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modelo é que você deve Refaça a arquitetura para uma arquitetura baseada em microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-131">The most important factor to consider if you migrate a full application to the [cloud-native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) model is that you must rearchitect to a microservices-based architecture.</span></span> <span data-ttu-id="a54b3-132">Isso exige um investimento significativo em desenvolvimento devido o grande refatoração processo envolvido.</span><span class="sxs-lookup"><span data-stu-id="a54b3-132">This clearly requires a significant investment in development because of the large refactoring process involved.</span></span> <span data-ttu-id="a54b3-133">Essa opção geralmente é escolhida para aplicativos de missão crítica que precisam de novos níveis de escalabilidade e agilidade de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-133">This option usually is chosen for mission-critical applications that need new levels of scalability and long-term agility.</span></span> <span data-ttu-id="a54b3-134">Mas, você pode começar a mover em direção à nuvem nativo adicionando microservices para apenas alguns novos cenários e eventualmente refatorar o aplicativo totalmente como microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-134">But, you could start moving toward cloud-native by adding microservices for just a few new scenarios, and eventually refactor the application fully as microservices.</span></span> <span data-ttu-id="a54b3-135">Esta é uma abordagem incremental que é a melhor opção para alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="a54b3-135">This is an incremental approach that is the best option for some scenarios.</span></span>

## <a name="what-about-microservices"></a><span data-ttu-id="a54b3-136">E microservices?</span><span class="sxs-lookup"><span data-stu-id="a54b3-136">What about microservices?</span></span> 

<span data-ttu-id="a54b3-137">Noções básicas sobre microservices e como eles funcionam é importante quando você estiver pensando em aplicativos de nuvem nativo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="a54b3-137">Understanding microservices and how they work is important when you are considering cloud-native applications for your organization.</span></span>

<span data-ttu-id="a54b3-138">A arquitetura de microservices é uma abordagem avançada que você pode usar para aplicativos que são criados do zero ou quando você desenvolve aplicativos existentes para aplicativos de nuvem nativo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-138">The microservices architecture is an advanced approach that you can use for applications that are created from scratch or when you evolve existing applications toward cloud-native applications.</span></span> <span data-ttu-id="a54b3-139">Você pode iniciar adicionando microservices alguns aplicativos existentes para saber mais sobre os novos paradigmas de microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-139">You can start by adding a few microservices to existing applications to learn about the new microservices paradigms.</span></span> <span data-ttu-id="a54b3-140">Mas, obviamente, você precisa arquiteto e código, especialmente para esse tipo de abordagem de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="a54b3-140">But clearly, you need to architect and code, especially for this type of architectural approach.</span></span>

<span data-ttu-id="a54b3-141">No entanto, microservices não são obrigatórios para qualquer aplicativo novo ou moderno.</span><span class="sxs-lookup"><span data-stu-id="a54b3-141">However, microservices are not mandatory for any new or modern application.</span></span> <span data-ttu-id="a54b3-142">Microservices não são um marcador"magic", e não são a maneira recomendada único de criar todos os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a54b3-142">Microservices are not a "magic bullet," and they aren't the single, best way to create every application.</span></span> <span data-ttu-id="a54b3-143">Como e quando você usar microservices depende do tipo de aplicativo que você precisa criar.</span><span class="sxs-lookup"><span data-stu-id="a54b3-143">How and when you use microservices depends on the type of application that you need to build.</span></span>

<span data-ttu-id="a54b3-144">A arquitetura microservices está se tornando a abordagem preferencial para aplicativos de missão crítica distribuídos e grandes ou complexas com base em vários subsistemas independentes na forma de serviços autônomos.</span><span class="sxs-lookup"><span data-stu-id="a54b3-144">The microservices architecture is becoming the preferred approach for distributed and large or complex mission-critical applications that are based on multiple, independent subsystems in the form of autonomous services.</span></span> <span data-ttu-id="a54b3-145">Em uma arquitetura baseada em microservices, um aplicativo é criado como uma coleção de serviços que podem ser desenvolvidos de forma independente, testada e com controle de versão, implantado e expandida.</span><span class="sxs-lookup"><span data-stu-id="a54b3-145">In a microservices-based architecture, an application is built as a collection of services that can be independently developed, tested, versioned, deployed, and scaled.</span></span> <span data-ttu-id="a54b3-146">Isso pode incluir qualquer banco de dados relacionado, autônomo por microsserviço.</span><span class="sxs-lookup"><span data-stu-id="a54b3-146">This can include any related, autonomous database per microservice.</span></span>

<span data-ttu-id="a54b3-147">Para obter uma visão detalhada de uma arquitetura de microservices que você pode implementar usando .NET Core, consulte para download PDF livro eletrônico [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook).</span><span class="sxs-lookup"><span data-stu-id="a54b3-147">For a detailed look at a microservices architecture that you can implement by using .NET Core, see the downloadable PDF e-book [.NET microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook).</span></span> <span data-ttu-id="a54b3-148">O guia também está disponível [online](../../microservices-architecture/index.md).</span><span class="sxs-lookup"><span data-stu-id="a54b3-148">The guide also is available [online](../../microservices-architecture/index.md).</span></span>

<span data-ttu-id="a54b3-149">Mas, mesmo em cenários em que microservices oferecem implantação de independente de recursos avançada, limites de subsistema de alta segurança e diversidade de tecnologia-elas também geram muitos novos desafios.</span><span class="sxs-lookup"><span data-stu-id="a54b3-149">But even in scenarios in which microservices offer powerful capabilities-independent deployment, strong subsystem boundaries, and technology diversity-they also raise many new challenges.</span></span> <span data-ttu-id="a54b3-150">Os desafios relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independente. Obtendo resiliente comunicação entre microservices; a necessidade de consistência eventual. e a complexidade operacional.</span><span class="sxs-lookup"><span data-stu-id="a54b3-150">The challenges are related to distributed application development, such as fragmented and independent data models; achieving resilient communication between microservices; the need for eventual consistency; and operational complexity.</span></span> <span data-ttu-id="a54b3-151">Microservices introduzir um nível mais alto de complexidade em comparação comparada aplicativos monolíticos tradicionais.</span><span class="sxs-lookup"><span data-stu-id="a54b3-151">Microservices introduce a higher level of complexity compared to traditional monolithic applications.</span></span>

<span data-ttu-id="a54b3-152">Devido à complexidade de uma arquitetura de microservices, somente determinados tipos de aplicativos e cenários específicos são adequados para aplicativos baseados em microsserviço.</span><span class="sxs-lookup"><span data-stu-id="a54b3-152">Because of the complexity of a microservices architecture, only specific scenarios and certain application types are suitable for microservice-based applications.</span></span> <span data-ttu-id="a54b3-153">Isso inclui aplicativos grandes e complexos que têm várias surgimento de subsistemas.</span><span class="sxs-lookup"><span data-stu-id="a54b3-153">These include large and complex applications that have multiple, evolving subsystems.</span></span> <span data-ttu-id="a54b3-154">Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para maior agilidade de longo prazo e manutenção de aplicativos mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="a54b3-154">In these cases, it's worth investing in a more complex software architecture, for increased long-term agility and more efficient application maintenance.</span></span> <span data-ttu-id="a54b3-155">Mas para cenários menos complexos, talvez seja melhor continuar com uma abordagem de aplicativo monolítico ou abordagens mais simples de N camadas.</span><span class="sxs-lookup"><span data-stu-id="a54b3-155">But for less complex scenarios, it might be better to continue with a monolithic application approach or simpler N-Tier approaches.</span></span>

<span data-ttu-id="a54b3-156">Como uma observação final, mesmo com o risco de ser repetitiva sobre esse conceito, você não deve examinar usando microservices em seus aplicativos como "completo ou nada."</span><span class="sxs-lookup"><span data-stu-id="a54b3-156">As a final note, even at the risk of being repetitive about this concept, you shouldn't look at using microservices in your applications as "all-in or nothing at all."</span></span> <span data-ttu-id="a54b3-157">Você pode estender e desenvolver aplicativos monolíticos existentes adicionando novos e cenários pequenos com base em microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-157">You can extend and evolve existing monolithic applications by adding new, small scenarios based on microservices.</span></span> <span data-ttu-id="a54b3-158">Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-158">You don't need to start from scratch to start working with a microservices architecture approach.</span></span> <span data-ttu-id="a54b3-159">Na verdade, é recomendável que você evoluir do uso de um aplicativo monolítico ou de N camadas existente adicionando novos cenários.</span><span class="sxs-lookup"><span data-stu-id="a54b3-159">In fact, we recommend that you evolve from using an existing monolithic or N-Tier application by adding new scenarios.</span></span> <span data-ttu-id="a54b3-160">Por fim, você pode dividir o aplicativo em componentes autônomos ou microservices.</span><span class="sxs-lookup"><span data-stu-id="a54b3-160">Eventually, you can break down the application into autonomous components or microservices.</span></span> <span data-ttu-id="a54b3-161">Você pode iniciar o surgimento de seus aplicativos monolíticos em direção microservices, passo a passo.</span><span class="sxs-lookup"><span data-stu-id="a54b3-161">You can start evolving your monolithic applications in a microservices direction, step by step.</span></span>

<span data-ttu-id="a54b3-162">Em qualquer caso, o restante deste guia presente concentra-se de tudo em "nenhum aplicativo baseado em microservices" porque este guia se destina principalmente modernização dos aplicativos existentes que normalmente têm arquiteturas monolíticos ou de N camadas.</span><span class="sxs-lookup"><span data-stu-id="a54b3-162">In any case, the rest of this present guidance focuses most of all on "no microservices-based apps" because this guidance is mainly targeting the modernization of existing apps that usually have monolithic or N-Tier architectures.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a54b3-163">[Anterior](microsoft-technologies-in-cloud-optimized-applications.md)
[Próximo](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="a54b3-163">[Previous](microsoft-technologies-in-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>