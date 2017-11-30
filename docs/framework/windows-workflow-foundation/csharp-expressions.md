---
title: "Expressões C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7d62d147bdc0177a28dbcc7d235f1c48dc51460
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="c-expressions"></a><span data-ttu-id="5bde9-102">Expressões C#</span><span class="sxs-lookup"><span data-stu-id="5bde9-102">C# Expressions</span></span>
<span data-ttu-id="5bde9-103">A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões C# têm suporte no [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bde9-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="5bde9-104">Novos projetos de fluxo de trabalho do C# criados no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] destinados ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usam expressões C# e os projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5bde9-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="5bde9-105">Os projetos de fluxo de trabalho existentes do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] que usam as expressões do Visual Basic podem ser migrados para o [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] independentemente da linguagem do projeto e têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5bde9-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="5bde9-106">Este tópico fornece uma visão geral de expressões C# no [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bde9-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="5bde9-107">Usando expressões C# em fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="5bde9-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="5bde9-108">Usando expressões c# no Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5bde9-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="5bde9-109">Versões anteriores compatibilidade</span><span class="sxs-lookup"><span data-stu-id="5bde9-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="5bde9-110">Usando expressões c# em fluxos de trabalho de código</span><span class="sxs-lookup"><span data-stu-id="5bde9-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="5bde9-111">Usando expressões c# em fluxos de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="5bde9-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="5bde9-112">Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="5bde9-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="5bde9-113">Xaml livre</span><span class="sxs-lookup"><span data-stu-id="5bde9-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="5bde9-114">Usando o c# expressões nos serviços de fluxo de trabalho XAMLX</span><span class="sxs-lookup"><span data-stu-id="5bde9-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <span data-ttu-id="5bde9-115"><a name="WFDesigner"></a>Usando expressões c# no Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5bde9-115"><a name="WFDesigner"></a> Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="5bde9-116">A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões C# têm suporte no [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bde9-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="5bde9-117">Projetos de fluxo de trabalho do C# criados no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] destinados ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usam expressões C#, enquanto que os projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5bde9-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="5bde9-118">Para especificar a expressão desejada do c#, digite-o na caixa rotulada **insira uma expressão de c#**.</span><span class="sxs-lookup"><span data-stu-id="5bde9-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="5bde9-119">Esse rótulo é exibido na janela de propriedades quando a atividade é selecionada no designer ou na atividade no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5bde9-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="5bde9-120">No exemplo a seguir, duas atividades `WriteLine` estão contidas no `Sequence` dentro de `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="5bde9-121">![Criado automaticamente atividade sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="5bde9-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bde9-122">As expressões C# têm suporte apenas no [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] e não têm suporte no designer de fluxo de trabalho hospedado novamente.</span><span class="sxs-lookup"><span data-stu-id="5bde9-122">C# expressions are supported only in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5bde9-123">novos recursos de WF45 têm suporte no designer de re-hospedado, consulte [suporte para recursos do novo fluxo de trabalho Foundation 4.5 no Designer de fluxo de trabalho hospedado novamente](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5bde9-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <span data-ttu-id="5bde9-124"><a name="BackwardCompat"></a>Versões anteriores compatibilidade</span><span class="sxs-lookup"><span data-stu-id="5bde9-124"><a name="BackwardCompat"></a> Backwards compatibility</span></span>  
 <span data-ttu-id="5bde9-125">As expressões do Visual Basic em projetos existentes de fluxo de trabalho do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# que foram migrados para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5bde9-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="5bde9-126">Quando as expressões do Visual Basic são exibidas no designer de fluxo de trabalho, o texto da expressão existente do Visual Basic é substituído por **valor foi definido em XAML**, a menos que a expressão do Visual Basic é uma sintaxe c# válida.</span><span class="sxs-lookup"><span data-stu-id="5bde9-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="5bde9-127">Se a expressão do Visual Basic for uma sintaxe C# válida, a expressão será exibida.</span><span class="sxs-lookup"><span data-stu-id="5bde9-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="5bde9-128">Para atualizar as expressões do Visual Basic para C#, você poderá editá-las no designer de fluxo de trabalho e especificar a expressão C# equivalente.</span><span class="sxs-lookup"><span data-stu-id="5bde9-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="5bde9-129">Não é necessário atualizar as expressões do Visual Basic para C#, mas, assim que as expressões forem atualizadas no designer de fluxo de trabalho, serão convertidas em C# e não poderão ser revertidas para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5bde9-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <span data-ttu-id="5bde9-130"><a name="CodeWorkflows"></a>Usando expressões c# em fluxos de trabalho de código</span><span class="sxs-lookup"><span data-stu-id="5bde9-130"><a name="CodeWorkflows"></a> Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="5bde9-131">As expressões C# têm suporte em fluxos de trabalho com base no código do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], mas antes que o fluxo de trabalho possa ser chamado, as expressões C# devem ser criadas usando <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bde9-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5bde9-132">Os autores de fluxo de trabalho podem usar `CSharpValue` para representar o valor r de uma expressão e `CSharpReference` para representar o valor l de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5bde9-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="5bde9-133">No exemplo a seguir, um fluxo de trabalho é criado com uma atividade `Assign` e uma atividade `WriteLine` contidas em uma atividade `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="5bde9-134">Um `CSharpReference` é especificado para o argumento `To` do `Assign`, e representa o valor l da expressão.</span><span class="sxs-lookup"><span data-stu-id="5bde9-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="5bde9-135">Um `CSharpValue` é especificado para o argumento `Value` do `Assign` e para o argumento `Text` do `WriteLine` e representa o valor r para essas duas expressões.</span><span class="sxs-lookup"><span data-stu-id="5bde9-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
```csharp  
Variable<int> n = new Variable<int>  
{  
    Name = "n"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { n },  
    Activities =  
    {  
        new Assign<int>  
        {  
            To = new CSharpReference<int>("n"),  
            Value = new CSharpValue<int>("new Random().Next(1, 101)")  
        },  
        new WriteLine  
        {  
            Text = new CSharpValue<string>("\"The number is \" + n")  
        }  
    }  
};  
  
CompileExpressions(wf);  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="5bde9-136">Depois que o fluxo de trabalho for criado, as expressões C# serão compiladas chamando o método auxiliar do `CompileExpressions` e, em seguida, o fluxo de trabalho será chamado.</span><span class="sxs-lookup"><span data-stu-id="5bde9-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="5bde9-137">O exemplo a seguir é o método `CompileExpressions`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-137">The following example is the `CompileExpressions` method.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="5bde9-138">Se as expressões c# não são compiladas, um <xref:System.NotSupportedException> é gerada quando o fluxo de trabalho é invocado com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' requer compilação para executar.</span><span class="sxs-lookup"><span data-stu-id="5bde9-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="5bde9-139">Certifique-se de que o fluxo de trabalho foi compilado.'</span><span class="sxs-lookup"><span data-stu-id="5bde9-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="5bde9-140">Se seu fluxo de trabalho baseado em código personalizado usar `DynamicActivity`, algumas alterações ao método `CompileExpressions` serão necessárias, como mostrado no seguinte exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="5bde9-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
```csharp  
static void CompileExpressions(DynamicActivity dynamicActivity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions. For Dynamic Activities this can be retrieved using the  
    // name property , which must be in the form Namespace.Type.  
    string activityName = dynamicActivity.Name;  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = dynamicActivity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = true  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(  
        dynamicActivity, compiledExpressionRoot);  
}  
```  
  
 <span data-ttu-id="5bde9-141">Há várias diferenças na sobrecarga do `CompileExpressions` que cria as expressões C# em uma atividade dinâmica.</span><span class="sxs-lookup"><span data-stu-id="5bde9-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="5bde9-142">O parâmetro para `CompileExpressions` é um `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="5bde9-143">O nome e o namespace do tipo são recuperados usando a propriedade `DynamicActivity.Name`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="5bde9-144">`TextExpressionCompilerSettings.ForImplementation` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="5bde9-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` é chamado em vez de `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="5bde9-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5bde9-146">Trabalhando com expressões no código, consulte [criação de fluxos de trabalho, atividades e expressões usando imperativo código](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="5bde9-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <span data-ttu-id="5bde9-147"><a name="XamlWorkflows"></a>Usando expressões c# em fluxos de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="5bde9-147"><a name="XamlWorkflows"></a> Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="5bde9-148">As expressões C# têm suporte em fluxos de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="5bde9-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="5bde9-149">Os fluxos de trabalho XAML compilados são criados em um tipo e os fluxos de trabalho XAML flexíveis são carregados pelo tempo de execução e compilados em uma árvore de atividade quando o fluxo de trabalho é executado.</span><span class="sxs-lookup"><span data-stu-id="5bde9-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="5bde9-150">Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="5bde9-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="5bde9-151">Xaml livre</span><span class="sxs-lookup"><span data-stu-id="5bde9-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <span data-ttu-id="5bde9-152"><a name="CompiledXaml"></a>Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="5bde9-152"><a name="CompiledXaml"></a> Compiled Xaml</span></span>  
 <span data-ttu-id="5bde9-153">As expressões C# têm suporte nos fluxos de trabalho XAML compilados criados em um tipo como parte de um projeto de fluxo de trabalho de C# destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bde9-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="5bde9-154">O XAML compilado é o tipo padrão de criação de fluxo de trabalho no [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] e os projetos de fluxo de trabalho de C# criados no [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] destinados para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usam expressões C#.</span><span class="sxs-lookup"><span data-stu-id="5bde9-154">Compiled XAML is the default type of workflow authoring in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and C# workflow projects created in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <span data-ttu-id="5bde9-155"><a name="LooseXaml"></a>Xaml livre</span><span class="sxs-lookup"><span data-stu-id="5bde9-155"><a name="LooseXaml"></a> Loose Xaml</span></span>  
 <span data-ttu-id="5bde9-156">As expressões C# têm suporte em fluxos de trabalho XAML flexíveis.</span><span class="sxs-lookup"><span data-stu-id="5bde9-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="5bde9-157">O programa do host de fluxo de trabalho que carrega e chama o fluxo de trabalho XAML flexível deve ser destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] e <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> devem ser definidos como `true` (o padrão é `false`).</span><span class="sxs-lookup"><span data-stu-id="5bde9-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="5bde9-158">Para definir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> como `true`, crie uma instância <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> com o conjunto de propriedades <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> definido como `true` e passá-lo como um parâmetro para <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bde9-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5bde9-159">Se `CompileExpressions` não está definido como `true`, um <xref:System.NotSupportedException> será lançada com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' requer compilação para executar.</span><span class="sxs-lookup"><span data-stu-id="5bde9-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="5bde9-160">Certifique-se de que o fluxo de trabalho foi compilado.'</span><span class="sxs-lookup"><span data-stu-id="5bde9-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5bde9-161">Trabalhando com fluxos de trabalho XAML, consulte [serializando fluxos de trabalho e atividades para e do XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5bde9-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <span data-ttu-id="5bde9-162"><a name="WFServices"></a>Usando o c# expressões nos serviços de fluxo de trabalho XAMLX</span><span class="sxs-lookup"><span data-stu-id="5bde9-162"><a name="WFServices"></a> Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="5bde9-163">Expressões C# têm suporte em serviços de fluxo de trabalho do XAMLX.</span><span class="sxs-lookup"><span data-stu-id="5bde9-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="5bde9-164">Quando um serviço de fluxo de trabalho é hospedado no IIS ou WAS, nenhuma etapa adicional é necessária. Porém, se o serviço de fluxo de trabalho XAML for auto-hospedado, as expressões C# deverão ser compiladas.</span><span class="sxs-lookup"><span data-stu-id="5bde9-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="5bde9-165">Para compilar as expressões c# em um serviço de fluxo de trabalho XAMLX auto-hospedado, primeiro carregar o arquivo de XAMLX em uma `WorkflowService`e, em seguida, passar o `Body` do `WorkflowService` para o `CompileExpressions` método descrito anteriormente na [usando c# expressões em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção.</span><span class="sxs-lookup"><span data-stu-id="5bde9-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="5bde9-166">No exemplo a seguir, um serviço de fluxo de trabalho XAMLX é carregado, as expressões C# são criadas e o serviço do fluxo de trabalho é aberto e aguarda solicitações.</span><span class="sxs-lookup"><span data-stu-id="5bde9-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
```csharp  
// Load the XAMLX workflow service.  
WorkflowService workflow1 =  
    (WorkflowService)XamlServices.Load(xamlxPath);  
  
// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.  
CompileExpressions(workflow1.Body);  
  
// Initialize the WorkflowServiceHost.  
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));  
  
// Enable Metadata publishing/  
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
smb.HttpGetEnabled = true;  
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;  
host.Description.Behaviors.Add(smb);  
  
// Open the WorkflowServiceHost and wait for requests.  
host.Open();  
Console.WriteLine("Press enter to quit");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="5bde9-167">Se as expressões C# não forem compiladas, a operação `Open` terá êxito, mas o fluxo de trabalho falhará quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="5bde9-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="5bde9-168">O seguinte `CompileExpressions` método é o mesmo que o método do anterior [usando c# expressões em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção.</span><span class="sxs-lookup"><span data-stu-id="5bde9-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```