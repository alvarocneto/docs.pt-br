---
title: "Como criar objetos gráficos para desenho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72f1af49a5c64395e018707d1f71cc0feaa2d22c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="3df94-102">Como criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="3df94-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="3df94-103">Antes que você possa desenhar linhas e formas, renderizar texto, ou exibir e manipular imagens com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você precisa criar um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="3df94-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3df94-104">O <xref:System.Drawing.Graphics> objeto representa um [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] superfície de desenho e é o objeto que é usado para criar imagens gráficas.</span><span class="sxs-lookup"><span data-stu-id="3df94-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="3df94-105">Há duas etapas ao trabalhar com gráficos:</span><span class="sxs-lookup"><span data-stu-id="3df94-105">There are two steps in working with graphics:</span></span>  
  
1.  <span data-ttu-id="3df94-106">Criando um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="3df94-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="3df94-107">Usando o <xref:System.Drawing.Graphics> objeto para desenhar linhas e formas, renderizar texto, ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="3df94-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="3df94-108">Criando um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="3df94-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="3df94-109">Um objeto gráfico pode ser criado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="3df94-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="3df94-110">Para criar um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="3df94-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="3df94-111">Receber uma referência a um objeto de gráfico como parte do <xref:System.Windows.Forms.PaintEventArgs> no <xref:System.Windows.Forms.Control.Paint> eventos de um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="3df94-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="3df94-112">Geralmente é assim que você obtém uma referência a um objeto gráfico ao criar código de pintura para um controle.</span><span class="sxs-lookup"><span data-stu-id="3df94-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="3df94-113">Da mesma forma, você também pode obter um objeto de gráfico como uma propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> ao tratar o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento para um <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="3df94-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="3df94-114">-ou-</span><span class="sxs-lookup"><span data-stu-id="3df94-114">-or-</span></span>  
  
-   <span data-ttu-id="3df94-115">Chamar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário.</span><span class="sxs-lookup"><span data-stu-id="3df94-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="3df94-116">Use esse método se quiser desenhar em um formulário ou controle que já exista.</span><span class="sxs-lookup"><span data-stu-id="3df94-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="3df94-117">-ou-</span><span class="sxs-lookup"><span data-stu-id="3df94-117">-or-</span></span>  
  
-   <span data-ttu-id="3df94-118">Criar um <xref:System.Drawing.Graphics> objeto a partir de qualquer objeto que herda de <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="3df94-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="3df94-119">Essa abordagem é útil quando você quer alterar uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="3df94-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="3df94-120">As seções a seguir dão detalhes sobre cada um desses processos.</span><span class="sxs-lookup"><span data-stu-id="3df94-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="3df94-121">PaintEventArgs no manipulador de eventos de pintura</span><span class="sxs-lookup"><span data-stu-id="3df94-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="3df94-122">Ao programar o <xref:System.Windows.Forms.PaintEventHandler> para controles ou <xref:System.Drawing.Printing.PrintDocument.PrintPage> para um <xref:System.Drawing.Printing.PrintDocument>, um objeto de gráfico é fornecido como uma das propriedades de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="3df94-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="3df94-123">Para obter uma referência a um objeto Gráfico de PaintEventArgs no evento de pintura</span><span class="sxs-lookup"><span data-stu-id="3df94-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1.  <span data-ttu-id="3df94-124">Declare o <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="3df94-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="3df94-125">Atribuir a variável para fazer referência a <xref:System.Drawing.Graphics> objeto passado como parte do <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="3df94-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3.  <span data-ttu-id="3df94-126">Inserir código para pintar o formulário ou o controle.</span><span class="sxs-lookup"><span data-stu-id="3df94-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="3df94-127">O exemplo a seguir mostra como referenciar um <xref:System.Drawing.Graphics> de objeto o <xref:System.Windows.Forms.PaintEventArgs> no <xref:System.Windows.Forms.Control.Paint> evento:</span><span class="sxs-lookup"><span data-stu-id="3df94-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="3df94-128">Método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="3df94-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="3df94-129">Você também pode usar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário.</span><span class="sxs-lookup"><span data-stu-id="3df94-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="3df94-130">Para criar um objeto gráfico com o método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="3df94-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="3df94-131">Chamar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método do formulário ou controle no qual você deseja renderizar elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="3df94-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="3df94-132">Criar de um objeto de imagem</span><span class="sxs-lookup"><span data-stu-id="3df94-132">Create from an Image Object</span></span>  
 <span data-ttu-id="3df94-133">Além disso, você pode criar um objeto de gráfico de qualquer objeto que deriva de <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="3df94-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="3df94-134">Para criar um objeto Gráfico de uma imagem</span><span class="sxs-lookup"><span data-stu-id="3df94-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="3df94-135">Chamar o <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> método, fornecendo o nome da variável a imagem da qual você deseja criar um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="3df94-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="3df94-136">O exemplo a seguir mostra como usar um <xref:System.Drawing.Bitmap> objeto:</span><span class="sxs-lookup"><span data-stu-id="3df94-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="3df94-137">Você só pode criar <xref:System.Drawing.Graphics> objetos de arquivos. bmp não indexados, como arquivos. bmp de 16 bits, 24 bits e 32 bits.</span><span class="sxs-lookup"><span data-stu-id="3df94-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="3df94-138">Cada pixel dos arquivos .bmp não indexados mantém uma cor, em contraste com pixels de arquivos .bmp indexados, que mantêm um índice para uma tabela de cores.</span><span class="sxs-lookup"><span data-stu-id="3df94-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="3df94-139">Desenhar e manipular imagens e formas</span><span class="sxs-lookup"><span data-stu-id="3df94-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="3df94-140">Depois que ele é criado, um <xref:System.Drawing.Graphics> objeto pode ser usado para desenhar linhas e formas, renderizar texto, ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="3df94-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="3df94-141">Os objetos principais que são usados com o <xref:System.Drawing.Graphics> objeto são:</span><span class="sxs-lookup"><span data-stu-id="3df94-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="3df94-142">O <xref:System.Drawing.Pen> classe — usado para desenhar linhas, contorno de formas ou processamento de outras representações geométricas.</span><span class="sxs-lookup"><span data-stu-id="3df94-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="3df94-143">O <xref:System.Drawing.Brush> classe — usado para preencher as áreas do gráfico, como texto, imagens ou formas preenchidas.</span><span class="sxs-lookup"><span data-stu-id="3df94-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="3df94-144">O <xref:System.Drawing.Font> classe — fornece uma descrição de quais formas para usar durante a renderização de texto.</span><span class="sxs-lookup"><span data-stu-id="3df94-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="3df94-145">O <xref:System.Drawing.Color> estrutura — representa as cores diferentes para exibir.</span><span class="sxs-lookup"><span data-stu-id="3df94-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="3df94-146">Para usar o objeto Gráfico que você criou</span><span class="sxs-lookup"><span data-stu-id="3df94-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="3df94-147">Trabalhe com o objeto apropriado listado acima para desenhar o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="3df94-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="3df94-148">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3df94-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="3df94-149">Para renderizar</span><span class="sxs-lookup"><span data-stu-id="3df94-149">To render</span></span>|<span data-ttu-id="3df94-150">Consulte</span><span class="sxs-lookup"><span data-stu-id="3df94-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="3df94-151">Linhas</span><span class="sxs-lookup"><span data-stu-id="3df94-151">Lines</span></span>|[<span data-ttu-id="3df94-152">Como desenhar uma linha em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3df94-152">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="3df94-153">Formas</span><span class="sxs-lookup"><span data-stu-id="3df94-153">Shapes</span></span>|[<span data-ttu-id="3df94-154">Como desenhar uma forma delineada</span><span class="sxs-lookup"><span data-stu-id="3df94-154">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="3df94-155">Texto</span><span class="sxs-lookup"><span data-stu-id="3df94-155">Text</span></span>|[<span data-ttu-id="3df94-156">Como desenhar texto em um Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3df94-156">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="3df94-157">Imagens</span><span class="sxs-lookup"><span data-stu-id="3df94-157">Images</span></span>|[<span data-ttu-id="3df94-158">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="3df94-158">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3df94-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df94-159">See Also</span></span>  
 [<span data-ttu-id="3df94-160">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="3df94-160">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="3df94-161">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3df94-161">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="3df94-162">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="3df94-162">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="3df94-163">Como Renderizar Imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="3df94-163">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)