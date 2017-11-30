---
title: "Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b9116cee8067ed3c7592413f30adc65379eb149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="5f43e-102">Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f43e-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="5f43e-103">permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX do ASP.NET que pode ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="5f43e-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="5f43e-104">Os procedimentos básicos para a criação de tais serviços é abordado em [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) e [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5f43e-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="5f43e-105">ASP.NET AJAX oferece suporte a operações que usam os verbos HTTP POST e HTTP GET, com HTTP POST, sendo o padrão.</span><span class="sxs-lookup"><span data-stu-id="5f43e-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="5f43e-106">Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca muda, use HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="5f43e-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="5f43e-107">Resultados das operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação poderão resultar em apenas uma solicitação ao serviço.</span><span class="sxs-lookup"><span data-stu-id="5f43e-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="5f43e-108">O armazenamento em cache não é feito por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , mas podem ocorrer em qualquer nível (em um navegador do usuário, em um servidor de proxy e outros níveis.) O cache é vantajoso para aumentar o desempenho do serviço, mas pode não ser aceitável se dados forem alterados com frequência ou se alguma ação de executar a operação.</span><span class="sxs-lookup"><span data-stu-id="5f43e-108">The caching is not done by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="5f43e-109">Por exemplo, se você estiver criando um serviço para gerenciar a biblioteca de música de um usuário, uma operação que procura artista com base em benefícios de título de um álbum usa GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar POST.</span><span class="sxs-lookup"><span data-stu-id="5f43e-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="5f43e-110">Para controlar o tempo de vida do cache, use o <xref:System.ServiceModel.Web.OutgoingWebResponseContext> tipo.</span><span class="sxs-lookup"><span data-stu-id="5f43e-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="5f43e-111">Por exemplo, durante a criação de um serviço que retorna a previsão atualizada a cada hora, você usaria obter mas limitar a duração do cache para uma hora ou menos para impedir que os usuários do serviço de acesso a dados obsoletos.</span><span class="sxs-lookup"><span data-stu-id="5f43e-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="5f43e-112">Ao usar os serviços de uma página AJAX ASP.NET que usam o controle do Gerenciador de Script, ele não faz diferença se usa a operação GET ou POST - o mecanismo de script do Gerenciador garante que o tipo de solicitação correto seja emitido.</span><span class="sxs-lookup"><span data-stu-id="5f43e-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="5f43e-113">Operações HTTP GET usam parâmetros de entrada com suporte a operações POST, incluindo tipos de contrato de dados complexos.</span><span class="sxs-lookup"><span data-stu-id="5f43e-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="5f43e-114">No entanto, na maioria dos casos é recomendável para evitar excesso de parâmetros ou parâmetros que são muito complexos em operações GET porque ele reduz a eficiência do cache.</span><span class="sxs-lookup"><span data-stu-id="5f43e-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="5f43e-115">Este tópico demonstra como selecionar entre GET e POST, adicionando o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para as operações relevantes no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5f43e-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="5f43e-116">As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para que o serviço em execução são semelhantes àquelas usadas por qualquer serviço ASP.NET AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f43e-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="5f43e-117">Uma operação marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> sempre usa uma solicitação GET.</span><span class="sxs-lookup"><span data-stu-id="5f43e-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="5f43e-118">Uma operação marcada com o <xref:System.ServiceModel.Web.WebInvokeAttribute>, ou não marcada com nenhum dos dois atributos, usa uma solicitação POST.</span><span class="sxs-lookup"><span data-stu-id="5f43e-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="5f43e-119">O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, outro que GET e POST (como PUT e DELETE) por meio de <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5f43e-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="5f43e-120">No entanto, esses verbos não têm suporte pelo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5f43e-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="5f43e-121">Se você pretende usar o serviço de páginas ASP.NET usando o controle do Gerenciador de Script, não use o <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5f43e-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="5f43e-122">Para obter um exemplo de funcionamento de alternar para GET, consulte o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="5f43e-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="5f43e-123">Para obter um exemplo que usa POST, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="5f43e-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="5f43e-124">Para criar um serviço WCF que responde a HTTP GET ou POST HTTP solicitações</span><span class="sxs-lookup"><span data-stu-id="5f43e-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>  
  
1.  <span data-ttu-id="5f43e-125">Definir um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato de serviço com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="5f43e-125">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="5f43e-126">Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5f43e-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="5f43e-127">Adicionar o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para estipular que uma operação deve responder a solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="5f43e-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="5f43e-128">Você também pode adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> de atributo para especificar explicitamente o HTTP POST ou não especificar um atributo, cujo padrão é HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="5f43e-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>  
  
    ```  
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="5f43e-129">Implementar o `IMusicService` contrato de serviço com um `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="5f43e-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  <span data-ttu-id="5f43e-130">Crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5f43e-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="5f43e-131">Editar esse arquivo adicionando apropriada [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço.</span><span class="sxs-lookup"><span data-stu-id="5f43e-131">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="5f43e-132">Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usada no [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5f43e-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a><span data-ttu-id="5f43e-133">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="5f43e-133">To call the service</span></span>  
  
1.  <span data-ttu-id="5f43e-134">Você pode testar as operações GET do serviço qualquer código de cliente, usando o navegador.</span><span class="sxs-lookup"><span data-stu-id="5f43e-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="5f43e-135">Por exemplo, se o serviço estiver configurado no endereço "http://example.com/service.svc", digitando "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" na barra de endereços do navegador chama o serviço e faz com que a resposta baixado ou exibido.</span><span class="sxs-lookup"><span data-stu-id="5f43e-135">For example, if your service is configured at the "http://example.com/service.svc" address, then typing "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>  
  
2.  <span data-ttu-id="5f43e-136">Você pode usar os serviços com operações GET da mesma maneira como outros serviços ASP.NET AJAX - inserindo o serviço de controlar o URL para a coleção de Scripts do Gerenciador de Script ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5f43e-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="5f43e-137">Para obter um exemplo, consulte o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="5f43e-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f43e-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f43e-138">See Also</span></span>  
 [<span data-ttu-id="5f43e-139">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="5f43e-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="5f43e-140">Como: migrar serviços Web do ASP.NET AJAX habilitado para o WCF</span><span class="sxs-lookup"><span data-stu-id="5f43e-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)