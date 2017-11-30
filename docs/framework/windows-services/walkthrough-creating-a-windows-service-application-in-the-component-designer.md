---
title: "Instruções passo a passo: criando um aplicativo de Serviço Windows no Designer de Componente"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
caps.latest.revision: "57"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: fb868aa38381294333538afcd99c030162d2f235
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a><span data-ttu-id="51dd4-102">Instruções passo a passo: criando um aplicativo de Serviço Windows no Designer de Componente</span><span class="sxs-lookup"><span data-stu-id="51dd4-102">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>
<span data-ttu-id="51dd4-103">Este artigo demonstra como criar um aplicativo simples de serviço Windows no Visual Studio que grava mensagens em um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="51dd4-103">This article demonstrates how to create a simple Windows Service application in Visual Studio that writes messages to an event log.</span></span> <span data-ttu-id="51dd4-104">Aqui estão as etapas básicas que podem ser executadas para criar e usar o serviço:</span><span class="sxs-lookup"><span data-stu-id="51dd4-104">Here are the basic steps that you perform to create and use your service:</span></span>  
  
1.  <span data-ttu-id="51dd4-105">[Criando um serviço](#BK_CreateProject) usando o **Windows Service** modelo de projeto e configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="51dd4-105">[Creating a Service](#BK_CreateProject) by using the **Windows Service** project template, and configure it.</span></span> <span data-ttu-id="51dd4-106">Esse modelo cria uma classe para você que é herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> e grava grande parte do código de serviço básico, como o código para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-106">This template creates a class for you that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> and writes much of the basic service code, such as the code to start the service.</span></span>  
  
2.  <span data-ttu-id="51dd4-107">[Adicionando recursos ao serviço](#BK_WriteCode) para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedimentos e substitua quaisquer outros métodos que você deseja redefinir.</span><span class="sxs-lookup"><span data-stu-id="51dd4-107">[Adding Features to the Service](#BK_WriteCode) for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures, and override any other methods that you want to redefine.</span></span>  
  
3.  <span data-ttu-id="51dd4-108">[Definir o Status do serviço](#BK_SetStatus).</span><span class="sxs-lookup"><span data-stu-id="51dd4-108">[Setting Service Status](#BK_SetStatus).</span></span> <span data-ttu-id="51dd4-109">Por padrão, serviços criados com <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementam apenas um subconjunto dos sinalizadores de status disponíveis.</span><span class="sxs-lookup"><span data-stu-id="51dd4-109">By default, services created with <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implement only a subset of the available status flags.</span></span> <span data-ttu-id="51dd4-110">Se o serviço levar muito tempo para iniciar, pausar ou interromper, você pode implementar os valores de status como Iniciar pendente ou Parar pendente para indicar que está funcionando em uma operação.</span><span class="sxs-lookup"><span data-stu-id="51dd4-110">If your service takes a long time to start up, pause, or stop, you can implement status values such as Start Pending or Stop Pending to indicate that it's working on an operation.</span></span>  
  
4.  <span data-ttu-id="51dd4-111">[Adicionando instaladores para o serviço](#BK_AddInstallers) para seu aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-111">[Adding Installers to the Service](#BK_AddInstallers) for your service application.</span></span>  
  
5.  <span data-ttu-id="51dd4-112">(Opcional) [Definir parâmetros de inicialização](#BK_StartupParameters), especificar argumentos de inicialização padrão e permitir que os usuários substituir as configurações padrão quando os usuários iniciarem o serviço manualmente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-112">(Optional) [Set Startup Parameters](#BK_StartupParameters), specify default startup arguments, and enable users to override default settings when they start your service manually.</span></span>  
  
6.  <span data-ttu-id="51dd4-113">[Criando o serviço](#BK_Build).</span><span class="sxs-lookup"><span data-stu-id="51dd4-113">[Building the Service](#BK_Build).</span></span>  
  
7.  <span data-ttu-id="51dd4-114">[Instalar o serviço](#BK_Install) no computador local.</span><span class="sxs-lookup"><span data-stu-id="51dd4-114">[Installing the Service](#BK_Install) on the local machine.</span></span>  
  
8.  <span data-ttu-id="51dd4-115">Acessar o Gerenciador de controle de serviço do Windows e [Iniciando e executando o serviço](#BK_StartService).</span><span class="sxs-lookup"><span data-stu-id="51dd4-115">Access the Windows Service Control Manager and [Starting and Running the Service](#BK_StartService).</span></span>  
  
9. <span data-ttu-id="51dd4-116">[Desinstalando um serviço do Windows](#BK_Uninstall).</span><span class="sxs-lookup"><span data-stu-id="51dd4-116">[Uninstalling a Windows Service](#BK_Uninstall).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="51dd4-117">O modelo de projeto dos Windows Services que é exigido para este passo a passo não está disponível na edição Express do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51dd4-117">The Windows Services project template that is required for this walkthrough is not available in the Express edition of Visual Studio.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a><span data-ttu-id="51dd4-118">Criando um serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-118">Creating a Service</span></span>  
 <span data-ttu-id="51dd4-119">Para começar, você cria o projeto e define valores que são exigidos para que o serviço funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-119">To begin, you create the project and set values that are required for the service to function correctly.</span></span>  
  
#### <a name="to-create-and-configure-your-service"></a><span data-ttu-id="51dd4-120">Para criar e configurar o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-120">To create and configure your service</span></span>  
  
1.  <span data-ttu-id="51dd4-121">No Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-121">In Visual Studio, on the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="51dd4-122">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="51dd4-122">The **New Project** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="51dd4-123">Na lista de modelos de projeto do Visual Basic ou Visual c#, escolha **Windows Service**e nomeie o projeto **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-123">In the list of Visual Basic or Visual C# project templates, choose **Windows Service**, and name the project **MyNewService**.</span></span> <span data-ttu-id="51dd4-124">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-124">Choose **OK**.</span></span>  
  
     <span data-ttu-id="51dd4-125">O modelo de projeto adiciona automaticamente uma classe de componente denominada `Service1` que é herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-125">The project template automatically adds a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="51dd4-126">Sobre o **editar** menu, escolha **localizar e substituir**, **localizar nos arquivos** (teclado: Ctrl + Shift + F).</span><span class="sxs-lookup"><span data-stu-id="51dd4-126">On the **Edit** menu, choose **Find and Replace**, **Find in Files** (Keyboard: Ctrl+Shift+F).</span></span> <span data-ttu-id="51dd4-127">Alterar todas as ocorrências de `Service1` para `MyNewService`.</span><span class="sxs-lookup"><span data-stu-id="51dd4-127">Change all occurrences of `Service1` to `MyNewService`.</span></span> <span data-ttu-id="51dd4-128">Você encontrará instâncias no Service1.cs, Program.cs e Service1.Designer.cs (ou seus equivalentes .vb).</span><span class="sxs-lookup"><span data-stu-id="51dd4-128">You’ll find instances in Service1.cs, Program.cs, and Service1.Designer.cs (or their .vb equivalents).</span></span>  
  
4.  <span data-ttu-id="51dd4-129">No **propriedades** janela para **Service1 [Design]** ou **Service1 [Design]**, defina o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> e **(nome)** propriedade `Service1` para **MyNewService**, se ainda não estiver definido.</span><span class="sxs-lookup"><span data-stu-id="51dd4-129">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> and the **(Name)** property for `Service1` to **MyNewService**, if it's not already set.</span></span>  
  
5.  <span data-ttu-id="51dd4-130">No Solution Explorer, renomeie **Service1.cs** para **MyNewService.cs**, ou **Service1** para **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-130">In Solution Explorer, rename **Service1.cs** to **MyNewService.cs**, or **Service1.vb** to **MyNewService.vb**.</span></span>  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a><span data-ttu-id="51dd4-131">Adicionando recursos ao serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-131">Adding Features to the Service</span></span>  
 <span data-ttu-id="51dd4-132">Na próxima seção, adicione um log de eventos personalizado ao serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="51dd4-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="51dd4-133">Os logs de eventos não são associados de forma alguma aos Windows Services.</span><span class="sxs-lookup"><span data-stu-id="51dd4-133">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="51dd4-134">Aqui o componente <xref:System.Diagnostics.EventLog> é usado como um exemplo do tipo de componente que você poderia adicionar a um Windows Service.</span><span class="sxs-lookup"><span data-stu-id="51dd4-134">Here the <xref:System.Diagnostics.EventLog> component is used as an example of the type of component you could add to a Windows service.</span></span>  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a><span data-ttu-id="51dd4-135">Para adicionar a funcionalidade de log de eventos personalizado ao seu serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-135">To add custom event log functionality to your service</span></span>  
  
1.  <span data-ttu-id="51dd4-136">Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Designer de exibição**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-136">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="51dd4-137">Do **componentes** seção o **caixa de ferramentas**, arraste um <xref:System.Diagnostics.EventLog> componente para o designer.</span><span class="sxs-lookup"><span data-stu-id="51dd4-137">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>  
  
3.  <span data-ttu-id="51dd4-138">Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-138">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>  
  
4.  <span data-ttu-id="51dd4-139">Adicione uma declaração para o **eventLog** objeto o `MyNewService` classe, logo após a linha que declara o `components` variável:</span><span class="sxs-lookup"><span data-stu-id="51dd4-139">Add a declaration for the **eventLog** object in the `MyNewService` class, right after the line that declares the `components` variable:</span></span>  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  <span data-ttu-id="51dd4-140">Adicione ou edite o construtor para definir um log de eventos personalizado:</span><span class="sxs-lookup"><span data-stu-id="51dd4-140">Add or edit the constructor to define a custom event log:</span></span>  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a><span data-ttu-id="51dd4-141">Para definir o que ocorre quando o serviço é iniciado</span><span class="sxs-lookup"><span data-stu-id="51dd4-141">To define what occurs when the service starts</span></span>  
  
-   <span data-ttu-id="51dd4-142">No Editor do Código, localize o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> que foi substituído automaticamente quando você criou o projeto e substitua o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="51dd4-142">In the Code Editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project, and replace the code with the following.</span></span> <span data-ttu-id="51dd4-143">Isso adiciona uma entrada no log de eventos quando o serviço começa a ser executado:</span><span class="sxs-lookup"><span data-stu-id="51dd4-143">This adds an entry to the event log when the service starts running:</span></span>  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     <span data-ttu-id="51dd4-144">Um aplicativo de serviço foi projetado para executado a longo prazo, por isso ele geralmente controla ou monitora algo no sistema.</span><span class="sxs-lookup"><span data-stu-id="51dd4-144">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="51dd4-145">O monitoramento é configurado no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-145">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="51dd4-146">No entanto, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> não realiza, de fato, o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="51dd4-146">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="51dd4-147">O método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> deve ser retornado ao sistema operacional depois que a operação do serviço tiver começado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-147">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="51dd4-148">Ele não deve fazer loop para sempre nem bloqueios.</span><span class="sxs-lookup"><span data-stu-id="51dd4-148">It must not loop forever or block.</span></span> <span data-ttu-id="51dd4-149">Para configurar um mecanismo de pesquisa simples, você pode usar o componente <xref:System.Timers.Timer?displayProperty=nameWithType> da seguinte forma: no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, defina os parâmetros no componente e, em seguida, defina a propriedade <xref:System.Timers.Timer.Enabled%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="51dd4-149">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="51dd4-150">O temporizador gera eventos no seu código periodicamente, no tempo em que seu serviço faria o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="51dd4-150">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="51dd4-151">Você pode usar o código a seguir para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="51dd4-151">You can use the following code to do this:</span></span>  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     <span data-ttu-id="51dd4-152">Adicione uma variável de membro para a classe.</span><span class="sxs-lookup"><span data-stu-id="51dd4-152">Add a member variable to the class.</span></span> <span data-ttu-id="51dd4-153">Ele conterá o identificador do próximo evento para gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="51dd4-153">It will contain the identifier of the next event to write into the event log.</span></span>

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     <span data-ttu-id="51dd4-154">Adicione o código para manipular o evento do temporizador:</span><span class="sxs-lookup"><span data-stu-id="51dd4-154">Add code to handle the timer event:</span></span>  
  
    ```csharp  
    public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)  
    {  
        // TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);  
    }  
    ```  
  
    ```vb  
    Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)  
        ' TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)  
        eventId = eventId + 1  
    End Sub  
    ```  
  
     <span data-ttu-id="51dd4-155">Você pode desejar executar tarefas usando segmentos de trabalho em segundo plano em vez de executar todo o seu trabalho no thread principal.</span><span class="sxs-lookup"><span data-stu-id="51dd4-155">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="51dd4-156">Para obter um exemplo disso, consulte a página de referência <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-156">For an example of this, see the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> reference page.</span></span>  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="51dd4-157">Para definir o que ocorre quando o serviço é interrompido</span><span class="sxs-lookup"><span data-stu-id="51dd4-157">To define what occurs when the service is stopped</span></span>  
  
-   <span data-ttu-id="51dd4-158">Substitua o código para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pelo seguinte.</span><span class="sxs-lookup"><span data-stu-id="51dd4-158">Replace the code for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method with the following.</span></span> <span data-ttu-id="51dd4-159">Isso adiciona uma entrada no log de eventos quando o serviço é interrompido:</span><span class="sxs-lookup"><span data-stu-id="51dd4-159">This adds an entry to the event log when the service is stopped:</span></span>  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 <span data-ttu-id="51dd4-160">Na próxima seção, você pode substituir os métodos <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> e <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> para definir o processamento adicional para o componente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-160">In the next section, you can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>  
  
#### <a name="to-define-other-actions-for-the-service"></a><span data-ttu-id="51dd4-161">Para definir outras ações para o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-161">To define other actions for the service</span></span>  
  
-   <span data-ttu-id="51dd4-162">Localize o método que deseja manipular, e substitua-o para definir o que você quer que aconteça.</span><span class="sxs-lookup"><span data-stu-id="51dd4-162">Locate the method that you want to handle, and override it to define what you want to occur.</span></span>  
  
     <span data-ttu-id="51dd4-163">O código a seguir mostra como você pode substituir o método <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>:</span><span class="sxs-lookup"><span data-stu-id="51dd4-163">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 <span data-ttu-id="51dd4-164">Algumas ações personalizadas precisam ocorrer quando um serviço Windows é instalado pela classe <xref:System.Configuration.Install.Installer>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-164">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="51dd4-165">O Visual Studio pode criar esses instaladores especificamente para um Windows Service e adicioná-los ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51dd4-165">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a><span data-ttu-id="51dd4-166">Definindo o status de serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-166">Setting Service Status</span></span>  
 <span data-ttu-id="51dd4-167">Serviços relatam seu status para o Gerenciador de Controle de Serviço, para que os usuários possam determinar se um serviço está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-167">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="51dd4-168">Por padrão, os serviços herdados de <xref:System.ServiceProcess.ServiceBase> relatam um conjunto limitado de configurações de status, inclusive Interrompido, Pausado e Em execução.</span><span class="sxs-lookup"><span data-stu-id="51dd4-168">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="51dd4-169">Se um serviço demora um pouco para inicializar, ele pode ser útil relatar um status Iniciar pendente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-169">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="51dd4-170">Você também pode implementar as configurações de status pendente iniciar e parar pendente, adicionando o código que chama o Windows [função SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).</span><span class="sxs-lookup"><span data-stu-id="51dd4-170">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).</span></span>  
  
#### <a name="to-implement-service-pending-status"></a><span data-ttu-id="51dd4-171">Para implementar o status pendente do serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-171">To implement service pending status</span></span>  
  
1.  <span data-ttu-id="51dd4-172">Adicione uma instrução `using` ou declaração `Imports` ao namespace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> no arquivo MyNewService.cs ou MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="51dd4-172">Add a `using` statement or `Imports` declaration to the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  <span data-ttu-id="51dd4-173">Adicione o seguinte código ao MyNewService.cs declarar os valores de `ServiceState` e para adicionar uma estrutura ao status, que você usará em uma chamada de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="51dd4-173">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>  
  
    ```csharp  
    public enum ServiceState  
      {  
          SERVICE_STOPPED = 0x00000001,  
          SERVICE_START_PENDING = 0x00000002,  
          SERVICE_STOP_PENDING = 0x00000003,  
          SERVICE_RUNNING = 0x00000004,  
          SERVICE_CONTINUE_PENDING = 0x00000005,  
          SERVICE_PAUSE_PENDING = 0x00000006,  
          SERVICE_PAUSED = 0x00000007,  
      }  
  
      [StructLayout(LayoutKind.Sequential)]  
      public struct ServiceStatus  
      {  
          public int dwServiceType;  
          public ServiceState dwCurrentState;  
          public int dwControlsAccepted;  
          public int dwWin32ExitCode;  
          public int dwServiceSpecificExitCode;  
          public int dwCheckPoint;  
          public int dwWaitHint;  
      };  
    ```  
  
    ```vb  
    Public Enum ServiceState  
        SERVICE_STOPPED = 1  
        SERVICE_START_PENDING = 2  
        SERVICE_STOP_PENDING = 3  
        SERVICE_RUNNING = 4  
        SERVICE_CONTINUE_PENDING = 5  
        SERVICE_PAUSE_PENDING = 6  
        SERVICE_PAUSED = 7  
    End Enum  
  
    <StructLayout(LayoutKind.Sequential)>  
    Public Structure ServiceStatus  
        Public dwServiceType As Long  
        Public dwCurrentState As ServiceState  
        Public dwControlsAccepted As Long  
        Public dwWin32ExitCode As Long  
        Public dwServiceSpecificExitCode As Long  
        Public dwCheckPoint As Long  
        Public dwWaitHint As Long  
    End Structure  
    ```  
  
3.  <span data-ttu-id="51dd4-174">Agora, no `MyNewService` classe, declare o [função SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) usando a plataforma chamar:</span><span class="sxs-lookup"><span data-stu-id="51dd4-174">Now, in the `MyNewService` class, declare the [SetServiceStatus function](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) by using platform invoke:</span></span>  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  <span data-ttu-id="51dd4-175">Para implementar o status Iniciar pendente, adicione o seguinte código ao início do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:</span><span class="sxs-lookup"><span data-stu-id="51dd4-175">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>  
  
    ```csharp  
    // Update the service state to Start Pending.  
    ServiceStatus serviceStatus = new ServiceStatus();  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;  
    serviceStatus.dwWaitHint = 100000;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Start Pending.  
    Dim serviceStatus As ServiceStatus = New ServiceStatus()  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING  
    serviceStatus.dwWaitHint = 100000  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
5.  <span data-ttu-id="51dd4-176">Adicione o código para definir o status Em execução no final do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-176">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>  
  
    ```csharp
    // Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
6.  <span data-ttu-id="51dd4-177">(Opcional) Repita esse procedimento para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-177">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="51dd4-178">O [Service Control Manager](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) usa o `dwWaitHint` e `dwCheckpoint` membros a [estrutura SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) para determinar o tempo de espera para um serviço do Windows iniciar ou desligar.</span><span class="sxs-lookup"><span data-stu-id="51dd4-178">The [Service Control Manager](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) to determine how much time to wait for a Windows Service to start or shut down.</span></span> <span data-ttu-id="51dd4-179">Se seu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> métodos de execução longa, o serviço pode solicitar mais tempo chamando [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) novamente com um incrementado `dwCheckPoint` valor.</span><span class="sxs-lookup"><span data-stu-id="51dd4-179">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) again with an incremented `dwCheckPoint` value.</span></span>  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a><span data-ttu-id="51dd4-180">Adicionando instaladores ao serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-180">Adding Installers to the Service</span></span>  
 <span data-ttu-id="51dd4-181">Antes de executar um serviço Windows, é necessário instalá-lo, o que o registra com o Gerenciador de Controle de Serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-181">Before you can run a Windows Service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="51dd4-182">Você pode adicionar instaladores ao seu projeto que lida com os detalhes de registro.</span><span class="sxs-lookup"><span data-stu-id="51dd4-182">You can add installers to your project that handle the registration details.</span></span>  
  
#### <a name="to-create-the-installers-for-your-service"></a><span data-ttu-id="51dd4-183">Para criar os instaladores para seu serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-183">To create the installers for your service</span></span>  
  
1.  <span data-ttu-id="51dd4-184">Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Designer de exibição**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-184">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="51dd4-185">Clique no plano de fundo do designer para selecionar o próprio serviço, e não um de seus conteúdos.</span><span class="sxs-lookup"><span data-stu-id="51dd4-185">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>  
  
3.  <span data-ttu-id="51dd4-186">Abra o menu de contexto para a janela do designer (se você estiver usando um dispositivo apontador, o botão direito do mouse dentro da janela) e, em seguida, escolha **adicionar instalador**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-186">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>  
  
     <span data-ttu-id="51dd4-187">Por padrão, uma classe de componente que contém dois instaladores é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="51dd4-187">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="51dd4-188">O componente é chamado **ProjectInstaller**e os instaladores que ele contém são o instalador para o serviço e o instalador para o serviço do processo associado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-188">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>  
  
4.  <span data-ttu-id="51dd4-189">Em **Design** exibir para **ProjectInstaller**, escolha **serviceInstaller1** para um projeto Visual c#, ou **ServiceInstaller1** para um Visual Projeto básico.</span><span class="sxs-lookup"><span data-stu-id="51dd4-189">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>  
  
5.  <span data-ttu-id="51dd4-190">No **propriedades** janela, certifique-se de <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> está definida como **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-190">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>  
  
6.  <span data-ttu-id="51dd4-191">Definir o **descrição** propriedade a um texto, como "Um exemplo de serviço".</span><span class="sxs-lookup"><span data-stu-id="51dd4-191">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="51dd4-192">Este texto é exibido na janela Serviços e ajuda o usuário a identificar o serviço e entender para que ele é usado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-192">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>  
  
7.  <span data-ttu-id="51dd4-193">Definir o <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> propriedade para o texto que você deseja exibir na janela Serviços no **nome** coluna.</span><span class="sxs-lookup"><span data-stu-id="51dd4-193">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="51dd4-194">Por exemplo, você pode inserir "Nome de exibição do MyNewService".</span><span class="sxs-lookup"><span data-stu-id="51dd4-194">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="51dd4-195">Esse nome pode ser diferente da propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, que é o nome usado pelo sistema (por exemplo, quando você usa o comando `net start` para iniciar o serviço).</span><span class="sxs-lookup"><span data-stu-id="51dd4-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>  
  
8.  <span data-ttu-id="51dd4-196">Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> como <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>  
  
     <span data-ttu-id="51dd4-197">![Propriedades de instalador para um serviço do Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="51dd4-197">![Installer Properties for a Windows Service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>  
  
9. <span data-ttu-id="51dd4-198">No designer, escolha **serviceProcessInstaller1** para um projeto Visual c#, ou **ServiceProcessInstaller1** para um projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="51dd4-198">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="51dd4-199">Defina a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> como <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-199">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="51dd4-200">Isso fará com que o serviço seja instalado e executado em uma conta de serviço local.</span><span class="sxs-lookup"><span data-stu-id="51dd4-200">This will cause the service to be installed and to run on a local service account.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="51dd4-201">A conta <xref:System.ServiceProcess.ServiceAccount.LocalSystem> tem amplas permissões, incluindo a capacidade de gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="51dd4-201">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="51dd4-202">Use essa conta com cuidado, pois ela pode aumentar o risco de ataques de software mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-202">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="51dd4-203">Para outras tarefas, pense em usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, que atua como um usuário não privilegiado no computador local e apresenta credenciais anônimas a qualquer servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="51dd4-203">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="51dd4-204">Este exemplo falhará se você tentar usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, pois ele precisa de permissão para gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="51dd4-204">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>  
  
     <span data-ttu-id="51dd4-205">Para obter mais informações sobre instaladores, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="51dd4-205">For more information about installers, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a><span data-ttu-id="51dd4-206">Defina os parâmetros de inicialização</span><span class="sxs-lookup"><span data-stu-id="51dd4-206">Set Startup Parameters</span></span>  
 <span data-ttu-id="51dd4-207">Um serviço Windows, como qualquer outro executável, pode aceitar argumentos de linha de comando ou parâmetros de inicialização.</span><span class="sxs-lookup"><span data-stu-id="51dd4-207">A Windows Service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="51dd4-208">Quando você adiciona o código aos parâmetros de inicialização do processo, os usuários podem iniciar o serviço com seus próprios parâmetros de inicialização personalizada usando a janela de Serviços no Painel de Controle do Windows.</span><span class="sxs-lookup"><span data-stu-id="51dd4-208">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="51dd4-209">No entanto, esses parâmetros de inicialização não são persistentes na próxima vez em que o serviço é iniciado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-209">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="51dd4-210">Para definir os parâmetros de inicialização permanentemente, você pode defini-las no registro, conforme mostrado neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="51dd4-210">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51dd4-211">Antes de decidir adicionar parâmetros de inicialização, considere se esta é a melhor maneira de passar informações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-211">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="51dd4-212">Embora os parâmetros de inicialização sejam fáceis de usar e analisar, e os usuários possam substituí-los facilmente, eles podem ser mais difíceis para os usuários descobrem e usarem sem a documentação.</span><span class="sxs-lookup"><span data-stu-id="51dd4-212">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="51dd4-213">Em geral, se o serviço exigir mais do que apenas alguns parâmetros de inicialização, você deve considerar usar o registro ou um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="51dd4-213">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="51dd4-214">Cada serviço Windows tem uma entrada no registro em HKLM\System\CurrentControlSet\services.</span><span class="sxs-lookup"><span data-stu-id="51dd4-214">Every Windows Service has an entry in the registry under HKLM\System\CurrentControlSet\services.</span></span> <span data-ttu-id="51dd4-215">Na chave do serviço, você pode usar o **parâmetros** subchave para armazenar informações que pode acessar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-215">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="51dd4-216">Você pode usar arquivos de configuração do aplicativo para um serviço Windows da mesma forma que faria para outros tipos de programas.</span><span class="sxs-lookup"><span data-stu-id="51dd4-216">You can use application configuration files for a Windows Service the same way you do for other types of programs.</span></span> <span data-ttu-id="51dd4-217">Para obter um exemplo de código, consulte <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-217">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>  
  
#### <a name="adding-startup-parameters"></a><span data-ttu-id="51dd4-218">Adicionando parâmetros de inicialização</span><span class="sxs-lookup"><span data-stu-id="51dd4-218">Adding startup parameters</span></span>  
  
1.  <span data-ttu-id="51dd4-219">No método `Main` no Program.cs ou MyNewService.Designer.vb, adicione um argumento da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="51dd4-219">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an argument for the command line:</span></span>  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  <span data-ttu-id="51dd4-220">Altere o construtor `MyNewService` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="51dd4-220">Change the `MyNewService` constructor as follows:</span></span>  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
    {
        logName = args[1];
    }
    eventLog1 = new System.Diagnostics.EventLog();
    if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
    {
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
    }
    eventLog1.Source = eventSourceName;
    eventLog1.Log = logName;        
}
```  
  
```vb  
Public Sub New(ByVal cmdArgs() As String)
    InitializeComponent()
    Dim eventSourceName As String = "MySource"
    Dim logName As String = "MyNewLog"
    If (cmdArgs.Count() > 0) Then
        eventSourceName = cmdArgs(0)
    End If
    If (cmdArgs.Count() > 1) Then
        logName = cmdArgs(1)
    End If
    eventLog1 = New System.Diagnostics.EventLog()
    If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
    End If
    eventLog1.Source = eventSourceName
    eventLog1.Log = logName
End Sub  
```  
  
<span data-ttu-id="51dd4-221">Esse código define o nome de origem e de log de eventos de acordo com os parâmetros de inicialização fornecidos ou usa os valores padrão se nenhum argumento for especificado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-221">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>  
  
3. <span data-ttu-id="51dd4-222">Para especificar os argumentos de linha de comando, adicione o seguinte código à classe `ProjectInstaller` em ProjectInstaller.cs ou ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="51dd4-222">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>  
  
```csharp  
protected override void OnBeforeInstall(IDictionary savedState)
{
    string parameter = "MySource1\" \"MyLogFile1";
    Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
    base.OnBeforeInstall(savedState);
}
```

```vb  
Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
    Dim parameter As String = "MySource1"" ""MyLogFile1"
    Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
    MyBase.OnBeforeInstall(savedState)
End Sub  
```  
  
<span data-ttu-id="51dd4-223">Esse código modifica o **ImagePath** chave do registro, que normalmente contém o caminho completo para o executável para o serviço do Windows, adicionando os valores de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="51dd4-223">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows Service, by adding the default parameter values.</span></span> <span data-ttu-id="51dd4-224">As aspas em torno do caminho (e em torno de cada parâmetro individual) são necessárias para o serviço ser inicializado corretamente.</span><span class="sxs-lookup"><span data-stu-id="51dd4-224">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="51dd4-225">Para alterar os parâmetros de inicialização para esse serviço do Windows, os usuários podem alterar os parâmetros fornecidos **ImagePath** chave do registro, embora a melhor maneira é alterá-la por meio de programação e expor a funcionalidade para usuários em um forma amigável (por exemplo, em um utilitário de configuração ou gerenciamento).</span><span class="sxs-lookup"><span data-stu-id="51dd4-225">To change the startup parameters for this Windows Service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a><span data-ttu-id="51dd4-226">Criando o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-226">Building the Service</span></span>  
  
#### <a name="to-build-your-service-project"></a><span data-ttu-id="51dd4-227">Para criar o projeto de serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-227">To build your service project</span></span>  
  
1.  <span data-ttu-id="51dd4-228">Em **Solution Explorer**, abra o menu de contexto para o seu projeto e, em seguida, escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-228">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span> <span data-ttu-id="51dd4-229">As páginas de propriedades do projeto são exibidas.</span><span class="sxs-lookup"><span data-stu-id="51dd4-229">The property pages for your project  appear.</span></span>  
  
2.  <span data-ttu-id="51dd4-230">Na guia do aplicativo, no **objeto de inicialização** , escolha **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-230">On the Application tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>  
  
3.  <span data-ttu-id="51dd4-231">Em **Solution Explorer**, abra o menu de contexto para o seu projeto e, em seguida, escolha **Build** para compilar o projeto (teclado: Ctrl + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="51dd4-231">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (Keyboard: Ctrl+Shift+B).</span></span>  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a><span data-ttu-id="51dd4-232">Instalando o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-232">Installing the Service</span></span>  
 <span data-ttu-id="51dd4-233">Agora que você criou o serviço Windows, poderá instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="51dd4-233">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="51dd4-234">Para instalar um serviço Windows, você deve ter credenciais administrativas no computador no qual está sendo instalado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-234">To install a Windows service, you must have administrative credentials on the computer on which you're installing it.</span></span>  
  
#### <a name="to-install-a-windows-service"></a><span data-ttu-id="51dd4-235">Para instalar um serviço Windows</span><span class="sxs-lookup"><span data-stu-id="51dd4-235">To install a Windows Service</span></span>  
  
1.  <span data-ttu-id="51dd4-236">No Windows 7 e Windows Server, abra o **Prompt de comando do desenvolvedor** em **ferramentas do Visual Studio** no **iniciar** menu.</span><span class="sxs-lookup"><span data-stu-id="51dd4-236">In Windows 7 and Windows Server, open the **Developer Command Prompt** under **Visual Studio Tools** in the **Start** menu.</span></span> <span data-ttu-id="51dd4-237">No Windows 8 ou Windows 8.1, escolha o **ferramentas do Visual Studio** bloco de **iniciar** tela e, em seguida, executar o Prompt de comando do desenvolvedor com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="51dd4-237">In Windows 8 or Windows 8.1, choose the **Visual Studio Tools** tile on the **Start** screen, and then run Developer Command Prompt with administrative credentials.</span></span> <span data-ttu-id="51dd4-238">(Se você estiver usando um mouse, clique duas vezes em **Prompt de comando do desenvolvedor**e, em seguida, escolha **executar como administrador**.)</span><span class="sxs-lookup"><span data-stu-id="51dd4-238">(If you’re using a mouse, right-click on **Developer Command Prompt**, and then choose **Run as Administrator**.)</span></span>  
  
2.  <span data-ttu-id="51dd4-239">Na janela do Prompt de comando, navegue até a pasta que contém a saída do projeto.</span><span class="sxs-lookup"><span data-stu-id="51dd4-239">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="51dd4-240">Por exemplo, na pasta Meus Documentos, navegue até Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="51dd4-240">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="51dd4-241">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="51dd4-241">Enter the following command:</span></span>  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     <span data-ttu-id="51dd4-242">Se o serviço for instalado com êxito, installutil.exe relatará o sucesso.</span><span class="sxs-lookup"><span data-stu-id="51dd4-242">If the service installs successfully, installutil.exe will report success.</span></span> <span data-ttu-id="51dd4-243">Se o sistema não puder localizar o InstallUtil.exe, certifique-se de que ela exista no seu computador.</span><span class="sxs-lookup"><span data-stu-id="51dd4-243">If the system could not find InstallUtil.exe, make sure that it exists on your computer.</span></span> <span data-ttu-id="51dd4-244">Essa ferramenta é instalada com o .NET Framework para a pasta `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*.</span><span class="sxs-lookup"><span data-stu-id="51dd4-244">This tool is installed with the .NET Framework to the folder `%WINDIR%\Microsoft.NET\Framework[64]\`*framework_version*.</span></span> <span data-ttu-id="51dd4-245">Por exemplo, é o caminho padrão para a versão de 32 bits do .NET Framework 4, 4.5, 4.5.1 e 4.5.2 é `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="51dd4-245">For example, the default path for the 32-bit version of the .NET Framework 4, 4.5, 4.5.1, and 4.5.2 is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span>  
  
     <span data-ttu-id="51dd4-246">Se o processo de installutil.exe relata falha, verifique o log de instalação para saber o motivo.</span><span class="sxs-lookup"><span data-stu-id="51dd4-246">If the installutil.exe process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="51dd4-247">Por padrão o log está na mesma pasta do executável do serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-247">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="51dd4-248">A instalação pode falhar se o <xref:System.ComponentModel.RunInstallerAttribute> classe não está presente no `ProjectInstaller` classe, caso contrário, o atributo não está definido como `true`, ou então `ProjectInstaller` a classe não é `public`.</span><span class="sxs-lookup"><span data-stu-id="51dd4-248">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, or else the attribute is not set to `true`, or else the `ProjectInstaller` class is not `public`.</span></span>  
  
     <span data-ttu-id="51dd4-249">Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="51dd4-249">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a><span data-ttu-id="51dd4-250">Iniciando e executando o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-250">Starting and Running the Service</span></span>  
  
#### <a name="to-start-and-stop-your-service"></a><span data-ttu-id="51dd4-251">Para iniciar e interromper o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-251">To start and stop your service</span></span>  
  
1.  <span data-ttu-id="51dd4-252">No Windows, abra o **iniciar** tela ou **iniciar** menu e tipo `services.msc`.</span><span class="sxs-lookup"><span data-stu-id="51dd4-252">In Windows, open the **Start** screen or **Start** menu, and type `services.msc`.</span></span>  
  
     <span data-ttu-id="51dd4-253">Agora você deve ver **MyNewService** listadas no **serviços** janela.</span><span class="sxs-lookup"><span data-stu-id="51dd4-253">You should now see **MyNewService** listed in the **Services** window.</span></span>  
  
     <span data-ttu-id="51dd4-254">![MyNewService na janela Serviços. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span><span class="sxs-lookup"><span data-stu-id="51dd4-254">![MyNewService in the Services window.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span></span>  
  
2.  <span data-ttu-id="51dd4-255">No **serviços** janela, abra o menu de atalho para o serviço e, em seguida, escolha **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-255">In the **Services** window, open the shortcut menu for your service, and then choose **Start**.</span></span>  
  
3.  <span data-ttu-id="51dd4-256">Abra o menu de atalho para o serviço e, em seguida, escolha **parar**.</span><span class="sxs-lookup"><span data-stu-id="51dd4-256">Open the shortcut menu for the service, and then choose **Stop**.</span></span>  
  
4.  <span data-ttu-id="51dd4-257">(Opcional) Na linha de comando, você pode usar os comandos `net start``ServiceName` e `net stop``ServiceName` para iniciar e parar o serviço.</span><span class="sxs-lookup"><span data-stu-id="51dd4-257">(Optional) From the command line, you can use the commands `net start``ServiceName` and `net stop``ServiceName` to start and stop your service.</span></span>  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a><span data-ttu-id="51dd4-258">Para verificar a saído do log de eventos do seu serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-258">To verify the event log output of your service</span></span>  
  
1.  <span data-ttu-id="51dd4-259">No Visual Studio, abra **Server Explorer** (teclado: Ctrl + Alt + S) e acessar o **Logs de eventos** nó para o computador local.</span><span class="sxs-lookup"><span data-stu-id="51dd4-259">In Visual Studio, open **Server Explorer** (Keyboard: Ctrl+Alt+S), and access the **Event Logs** node for the local computer.</span></span>  
  
2.  <span data-ttu-id="51dd4-260">Localize a listagem para **MyNewLog** (ou **MyLogFile1**, se você usou o procedimento opcional para adicionar argumentos de linha de comando) e expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="51dd4-260">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you used the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="51dd4-261">Você deverá ver entradas para as duas ações (iniciar e parar) que seu serviço executou.</span><span class="sxs-lookup"><span data-stu-id="51dd4-261">You should see entries for the two actions (start and stop) your service has performed.</span></span>  
  
     <span data-ttu-id="51dd4-262">![Use o Visualizador de eventos para ver as entradas de log de eventos. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span><span class="sxs-lookup"><span data-stu-id="51dd4-262">![Use the Event Viewer to see the event log entries.](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span></span>  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a><span data-ttu-id="51dd4-263">Desinstalando um serviço Windows</span><span class="sxs-lookup"><span data-stu-id="51dd4-263">Uninstalling a Windows Service</span></span>  
  
#### <a name="to-uninstall-your-service"></a><span data-ttu-id="51dd4-264">Para desinstalar o serviço</span><span class="sxs-lookup"><span data-stu-id="51dd4-264">To uninstall your service</span></span>  
  
1.  <span data-ttu-id="51dd4-265">Abra um prompt de comando do desenvolvedor com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="51dd4-265">Open a developer command prompt with administrative credentials.</span></span>  
  
2.  <span data-ttu-id="51dd4-266">Na janela do Prompt de comando, navegue até a pasta que contém a saída do projeto.</span><span class="sxs-lookup"><span data-stu-id="51dd4-266">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="51dd4-267">Por exemplo, na pasta Meus Documentos, navegue até Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="51dd4-267">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="51dd4-268">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="51dd4-268">Enter the following command:</span></span>  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     <span data-ttu-id="51dd4-269">Se o serviço for desinstalado com êxito, installutil.exe relatará que seu serviço foi removido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="51dd4-269">If the service uninstalls successfully, installutil.exe will report that your service was successfully removed.</span></span> <span data-ttu-id="51dd4-270">Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="51dd4-270">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="51dd4-271">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="51dd4-271">Next Steps</span></span>  
 <span data-ttu-id="51dd4-272">Você pode criar um programa de instalação autônomo que outras pessoas podem usar para instalar o serviço Windows, mas ele necessita de etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="51dd4-272">You can create a standalone setup program that others can use to install your Windows service, but it requires additional steps.</span></span> <span data-ttu-id="51dd4-273">O ClickOnce não oferece suporte aos Windows Services, de modo que não é possível usar o Assistente de Publicação.</span><span class="sxs-lookup"><span data-stu-id="51dd4-273">ClickOnce doesn't support Windows services, so you can't use the Publish Wizard.</span></span> <span data-ttu-id="51dd4-274">Você pode usar a edição completa do InstallShield, que não é fornecido pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="51dd4-274">You can use a full edition of InstallShield, which Microsoft doesn't provide.</span></span> <span data-ttu-id="51dd4-275">Para obter mais informações sobre o InstallShield, consulte [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span><span class="sxs-lookup"><span data-stu-id="51dd4-275">For more information about InstallShield, see [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span></span> <span data-ttu-id="51dd4-276">Você também pode usar o [o conjunto de ferramentas do Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=249067) para criar um instalador para um serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="51dd4-276">You can also use the [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=249067) to create an installer for a Windows service.</span></span>  
  
 <span data-ttu-id="51dd4-277">Você pode explorar o uso de um componente <xref:System.ServiceProcess.ServiceController> para permitir que você envie comandos ao serviço que instalou.</span><span class="sxs-lookup"><span data-stu-id="51dd4-277">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you have installed.</span></span>  
  
 <span data-ttu-id="51dd4-278">É possível usar um instalador para criar um log de eventos quando o aplicativo é instalado, em vez de criá-lo quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-278">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="51dd4-279">Além disso, o log de eventos será excluído pelo instalador quando o aplicativo for desinstalado.</span><span class="sxs-lookup"><span data-stu-id="51dd4-279">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="51dd4-280">Para obter mais informações, consulte a página de referência <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="51dd4-280">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dd4-281">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51dd4-281">See Also</span></span>  
 [<span data-ttu-id="51dd4-282">Aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="51dd4-282">Windows Service Applications</span></span>](../../../docs/framework/windows-services/index.md)  
 [<span data-ttu-id="51dd4-283">Introdução aos aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="51dd4-283">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="51dd4-284">Como: depurar aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="51dd4-284">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="51dd4-285">Serviços (Windows)</span><span class="sxs-lookup"><span data-stu-id="51dd4-285">Services (Windows)</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)