---
title: Interfaces (F#)
description: 'Saiba como Interfaces de F # especificar conjuntos de membros relacionados que implementam de outras classes.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a082459-17d4-45cf-9153-0b7550a154ec
ms.openlocfilehash: d7c95e5f5cc0bc6c7f6393af990427ac491c5b79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="9de8c-104">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9de8c-104">Interfaces</span></span>

<span data-ttu-id="9de8c-105">*Interfaces* especificar conjuntos de membros relacionados que implementam de outras classes.</span><span class="sxs-lookup"><span data-stu-id="9de8c-105">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="9de8c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9de8c-106">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="9de8c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9de8c-107">Remarks</span></span>
<span data-ttu-id="9de8c-108">Declarações de interface parecida com declarações de classe, exceto que os membros não são implementados.</span><span class="sxs-lookup"><span data-stu-id="9de8c-108">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="9de8c-109">Em vez disso, todos os membros são abstratos, conforme indicado pela palavra-chave `abstract`.</span><span class="sxs-lookup"><span data-stu-id="9de8c-109">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="9de8c-110">Você não fornecer um corpo de método para métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="9de8c-110">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="9de8c-111">No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com o `default` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9de8c-111">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="9de8c-112">Isso é equivalente à criação de um método virtual em uma classe base em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="9de8c-112">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="9de8c-113">Esse é um método virtual pode ser substituído nas classes que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="9de8c-113">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="9de8c-114">Você pode, opcionalmente, nomeie cada parâmetro de método usando a sintaxe normal do F #:</span><span class="sxs-lookup"><span data-stu-id="9de8c-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="9de8c-115">Em acima `ISprintable` exemplo, o `Print` método tem um único parâmetro do tipo `string` com o nome `format`.</span><span class="sxs-lookup"><span data-stu-id="9de8c-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="9de8c-116">Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="9de8c-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="9de8c-117">Em ambos os casos, a expressão de tipo ou objeto de classe fornece corpos de métodos abstratos da interface.</span><span class="sxs-lookup"><span data-stu-id="9de8c-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="9de8c-118">Implementações são específicas para cada tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="9de8c-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="9de8c-119">Portanto, os métodos de interface em tipos diferentes podem ser diferentes uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="9de8c-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="9de8c-120">As palavras-chave `interface` e `end`, que marca o início e fim da definição, são opcionais quando você usa a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="9de8c-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="9de8c-121">Se você não usa essas palavras-chave, o compilador tenta inferir se o tipo é uma classe ou uma interface, analisando as construções que você usa.</span><span class="sxs-lookup"><span data-stu-id="9de8c-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="9de8c-122">Se você define um membro ou use outra sintaxe de classe, o tipo é interpretado como uma classe.</span><span class="sxs-lookup"><span data-stu-id="9de8c-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="9de8c-123">O estilo de codificação de .NET é começar a todas as interfaces com uma letra maiuscula `I`.</span><span class="sxs-lookup"><span data-stu-id="9de8c-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="9de8c-124">Implementando Interfaces usando tipos de classe</span><span class="sxs-lookup"><span data-stu-id="9de8c-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="9de8c-125">Você pode implementar uma ou mais interfaces em um tipo de classe usando o `interface` palavra-chave, o nome da interface e o `with` palavra-chave, seguido de definições de membro de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9de8c-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="9de8c-126">Implementações de interface são herdadas, não é necessário que todas as classes derivadas reimplementá-los.</span><span class="sxs-lookup"><span data-stu-id="9de8c-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="9de8c-127">Chamando métodos de Interface</span><span class="sxs-lookup"><span data-stu-id="9de8c-127">Calling Interface Methods</span></span>
<span data-ttu-id="9de8c-128">Métodos de interface podem ser chamados somente por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="9de8c-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="9de8c-129">Portanto, talvez você precise elevação para o tipo de interface usando o `:>` operador ou a `upcast` operador para chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="9de8c-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="9de8c-130">Para chamar o método de interface quando você tiver um objeto do tipo `SomeClass`, você deve upcast o objeto para o tipo de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9de8c-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="9de8c-131">Uma alternativa é para declarar um método no objeto que upcasts e chama o método de interface, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9de8c-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="9de8c-132">Implementando Interfaces usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="9de8c-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="9de8c-133">Expressões de objeto fornecem uma maneira curta para implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="9de8c-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="9de8c-134">Eles são úteis quando você não precisa criar um tipo nomeado, e você quiser apenas um objeto que oferece suporte os métodos de interface, sem qualquer métodos adicionais.</span><span class="sxs-lookup"><span data-stu-id="9de8c-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="9de8c-135">Uma expressão de objeto é ilustrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9de8c-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="9de8c-136">Herança de interface</span><span class="sxs-lookup"><span data-stu-id="9de8c-136">Interface Inheritance</span></span>
<span data-ttu-id="9de8c-137">Interfaces podem herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="9de8c-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9de8c-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9de8c-138">See Also</span></span>
[<span data-ttu-id="9de8c-139">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="9de8c-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9de8c-140">Expressões de Objeto</span><span class="sxs-lookup"><span data-stu-id="9de8c-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="9de8c-141">Classes</span><span class="sxs-lookup"><span data-stu-id="9de8c-141">Classes</span></span>](classes.md)