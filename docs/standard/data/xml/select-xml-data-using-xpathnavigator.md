---
title: Selecionar dados XML usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070507"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Selecionar dados XML usando XPathNavigator
A classe <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para selecionar um conjunto de nós em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> usando uma expressão XPath. Depois de selecionado, você pode iterar sobre o conjunto de nós selecionado.  
  
## <a name="xpathnavigator-selection-methods"></a>Métodos de seleção XPathNavigator  
 A classe <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para selecionar um conjunto de nós em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> usando uma expressão XPath. A classe <xref:System.Xml.XPath.XPathNavigator> também fornece um conjunto de métodos otimizados para selecionar nós ancestrais, filhos ou descendentes mais rapidamente do que usar uma expressão XPath. O conjunto de nós selecionado é retornado em um objeto <xref:System.Xml.XPath.XPathNodeIterator> ou em um objeto <xref:System.Xml.XPath.XPathNavigator> no caso de um único nó selecionado.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Selecionando nós usando expressões XPath  
 Para selecionar um conjunto de nós usando uma expressão XPath, use um dos seguintes métodos de seleção.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Quando chamados, esses métodos retornam um conjunto de nós que você pode navegar livremente usando um objeto <xref:System.Xml.XPath.XPathNodeIterator> ou um objeto <xref:System.Xml.XPath.XPathNavigator> no caso de um único nó selecionado.  
  
 A navegação com um objeto <xref:System.Xml.XPath.XPathNodeIterator> não afeta a posição do objeto <xref:System.Xml.XPath.XPathNavigator> usado para criá-lo. O objeto <xref:System.Xml.XPath.XPathNavigator> retornado dos métodos <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> é posicionado no único nó retornado e também não afeta a posição do objeto <xref:System.Xml.XPath.XPathNavigator> usado para criá-lo.  
  
 O exemplo a seguir mostra a criação de um objeto <xref:System.Xml.XPath.XPathNavigator> de um objeto <xref:System.Xml.XPath.XPathDocument>, o uso do método <xref:System.Xml.XPath.XPathNavigator.Select%2A> para selecionar nós no objeto <xref:System.Xml.XPath.XPathDocument> e o uso do objeto <xref:System.Xml.XPath.XPathNodeIterator> para iterar sobre os nós selecionados.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 O exemplo usa o arquivo `books.xml` como entrada.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Métodos de seleção otimizados  
 Os métodos <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> e <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> da classe <xref:System.Xml.XPath.XPathNavigator> representam as expressões XPath comumente usadas para recuperar os nós filho, descendentes e ancestrais. Esses métodos são otimizados para desempenho e são mais rápidos do que as expressões XPath correspondentes. Os métodos <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> e <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> selecionam os nós ancestrais, filho e descendentes com base em um valor <xref:System.Xml.XPath.XPathNodeType> ou o nome local e o URI do namespace dos nós a serem selecionados. Os nós ancestrais, filho e descendentes selecionados são retornados em um objeto <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Avaliar as expressões XPath usando XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [Correspondência de nós usando XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [Tipos de nós reconhecidos com consultas XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [Consultas e Namespaces de XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [Expressões XPath compilados](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
