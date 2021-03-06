---
title: Genéricos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 638612a0ece8e701b088c97e5dfc49362e6d6419
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506075"
---
# <a name="generics-c-programming-guide"></a>Genéricos (Guia de Programação em C#)
Genéricos foram adicionados à versão 2.0 da linguagem C# e o common language runtime (CLR). Genéricos apresentam ao .NET Framework o conceito de parâmetros de tipo, que possibilitam a criação de classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou método seja declarado e instanciado pelo código do cliente. Por exemplo, ao usar um parâmetro de tipo genérico T, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer o custo ou corre o risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Visão geral de genéricos  
  
-   Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.  
  
-   O uso mais comum de genéricos é para criar classes de coleção.  
  
-   A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>. Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.  
  
-   Você pode criar suas próprias interfaces genéricas, classes, métodos, eventos e delegados.  
  
-   Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.  
  
-   Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Benefícios dos genéricos](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Parâmetros de tipo genérico](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Interfaces genéricas](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Delegados genéricos](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Diferenças entre modelos C++ e genéricos C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Genéricos e reflexão](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 Para obter mais informações, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Tipos](../../../csharp/programming-guide/types/index.md)  
- [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [Genéricos no .NET](../../../standard/generics/index.md)  