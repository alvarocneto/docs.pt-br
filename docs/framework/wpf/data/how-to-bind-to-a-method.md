---
title: "Como associar a um método"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c276e9da3eaaf786038a117532848364b03e9b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="bc1c4-102">Como associar a um método</span><span class="sxs-lookup"><span data-stu-id="bc1c4-102">How to: Bind to a Method</span></span>
<span data-ttu-id="bc1c4-103">O exemplo a seguir mostra como associar a um método usando <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc1c4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc1c4-104">Example</span></span>  
 <span data-ttu-id="bc1c4-105">Neste exemplo, `TemperatureScale` é uma classe que tem um método `ConvertTemp`, que usa dois parâmetros (um do tipo `double` e outro do tipo `enum` `TempType)` e converte o valor dado de uma escala de temperatura em outra.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="bc1c4-106">No exemplo a seguir, uma <xref:System.Windows.Data.ObjectDataProvider> é usado para instanciar o `TemperatureScale` objeto.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="bc1c4-107">O método `ConvertTemp` é chamado com dois parâmetros especificados.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="bc1c4-108">Agora que o método está disponível como um recurso, é possível associar aos seus resultados.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="bc1c4-109">No exemplo a seguir, o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade o <xref:System.Windows.Controls.TextBox> e o <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> do <xref:System.Windows.Controls.ComboBox> estão associados aos dois parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="bc1c4-110">Isso permite que os usuários especifiquem a temperatura a ser convertida e a escala de conversão.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="bc1c4-111">Observe que <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> é definido como `true` porque estamos ligando o <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> propriedade do <xref:System.Windows.Data.ObjectDataProvider> instância e não propriedades do objeto encapsulados pelo <xref:System.Windows.Data.ObjectDataProvider> (o `TemperatureScale` objeto).</span><span class="sxs-lookup"><span data-stu-id="bc1c4-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="bc1c4-112">O <xref:System.Windows.Controls.ContentControl.Content%2A> da última <xref:System.Windows.Controls.Label> atualiza quando o usuário modifica o conteúdo do <xref:System.Windows.Controls.TextBox> ou a seleção do <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="bc1c4-113">O conversor `DoubleToString` usa double e a transforma em uma cadeia de caracteres a <xref:System.Windows.Data.IValueConverter.Convert%2A> direção (da fonte de associação para o destino da associação, que é o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade) e converte um `string` para um `double` no <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direção.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="bc1c4-114">O `InvalidationCharacterRule` é um <xref:System.Windows.Controls.ValidationRule> que verifica se há caracteres inválidos.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="bc1c4-115">O modelo de erro padrão, que é uma borda vermelha ao redor do <xref:System.Windows.Controls.TextBox>, é exibido notificar os usuários quando o valor de entrada não é um valor duplo.</span><span class="sxs-lookup"><span data-stu-id="bc1c4-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1c4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc1c4-116">See Also</span></span>  
 [<span data-ttu-id="bc1c4-117">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="bc1c4-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="bc1c4-118">Associar a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="bc1c4-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)