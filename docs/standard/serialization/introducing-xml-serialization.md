---
title: "Apresentando a serialização XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
caps.latest.revision: 8
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 858d973ae48ee217f73f293c1ed30c4c3f91cb29
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="introducing-xml-serialization"></a>Apresentando a serialização XML
A serialização é o processo de conversão de um objeto em um formulário que possa ser prontamente transportado. Por exemplo, você pode serializar um objeto e transportá-lo pela Internet usando HTTP entre um cliente e um servidor. Na outra extremidade, a desserialização reconstrói o objeto a partir do fluxo.  
  
 A serialização XML serializa apenas os valores de propriedades e de campos públicos de um objeto em um fluxo XML. A serialização XML não inclui informações de tipo. Por exemplo, se você tiver um objeto **Book** no namespace **Library**, não haverá garantia de que ele será desserializado em um objeto do mesmo tipo.  
  
> [!NOTE]
>  A serialização XML não converte métodos, indexadores, campos privados nem propriedades somente leitura (exceto coleções somente leitura). Para serializar todos os campos e propriedades (públicos e privados) de um objeto, use <xref:System.Runtime.Serialization.DataContractSerializer>, em vez da serialização XML.  
  
 A classe central na serialização XML é a classe <xref:System.Xml.Serialization.XmlSerializer> e os métodos mais importantes nessa classe são os métodos **Serialize** e **Deserialize**. O <xref:System.Xml.Serialization.XmlSerializer> cria arquivos C# e compila-os em arquivos .dll para executar essa serialização. No .NET Framework 2.0, a [Ferramenta Geradora de Serializador XML (Sgen.exe)](../../../docs/standard/serialization/xml-serializer-generator-tool-sgen-exe.md) tem como objetivo gerar com antecedência esses assemblies de serialização a serem implantados com seu aplicativo e melhorar o desempenho da inicialização. O fluxo XML gerado pelo **XmlSerializer** é em conformidade com a recomendação XSD (linguagem de definição de esquema XML) 1.0 do World Wide Web Consortium (www.w3.org). Além disso, os tipos de dados gerados são compatíveis com o documento intitulado "XML Schema Part 2: Datatypes".  
  
 Os dados em seus objetos são descritos com o uso de construções de linguagem de programação como classes, campos, propriedades, tipos primitivos, matrizes e até mesmo XML inserido na forma de objetos **XmlElement** ou **XmlAttribute**. Você tem a opção de criar suas próprias classes, anotadas com atributos, ou de usar a ferramenta de definição de esquema XML para gerar as classes com base em um esquema XML existente.  
  
 Se você tiver um esquema XML, poderá executar a ferramenta de definição de esquema XML para gerar um conjunto de classes fortemente tipadas para o esquema e anotadas com atributos. Quando uma instância desse tipo de classe é serializada, o XML adere ao esquema XML. Se você tiver uma classe desse tipo, poderá programar com um modelo de objeto facilmente manipulado com a certeza de que o XML gerado está de acordo com o esquema XML. Trata-se de uma alternativa ao uso de outras classes do .NET Framework, tais como as classes **XmlReader** e **XmlWriter**, para analisar e gravar um fluxo XML. Para obter mais informações, consulte [Documentos e dados XML](../../../docs/standard/data/xml/index.md). Essas classes permitem analisar qualquer fluxo XML. Em contraste, use **XmlSerializer** quando o fluxo XML precisar estar em conformidade com um esquema XML conhecido.  
  
 Os atributos controlam o fluxo XML gerado pela classe **XmlSerializer**, permitindo que você defina itens do fluxo XML, como o namespace de XML, o nome do elemento, o nome do atributo e assim por diante. Para obter mais informações sobre como esses atributos e como eles controlam a serialização XML, consulte [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md). Para ver uma tabela desses atributos que são usados para controlar o XML gerado, consulte [Atributos que controlam a serialização XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).  
  
 A classe **XmlSerializer** pode serializar ainda mais um objeto e gerar um fluxo XML SOAP codificado. O XML gerado adere à seção 5 do documento "Simple Object Access Protocol (SOAP) 1.1" do World Wide Web Consortium. Para obter mais informações sobre esse processo, consulte [Como serializar um objeto como um fluxo XML codificado para SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Para ver uma tabela dos atributos que controlam o XML gerado, consulte [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 A classe **XmlSerializer** gera as mensagens SOAP criadas por serviços Web XML e passadas para eles. Para controlar as mensagens SOAP, você pode aplicar atributos às classes, aos valores de retorno, aos parâmetros e aos campos localizados em um arquivo de serviço Web XML (.asmx). É possível usar ambos os atributos listados em "Atributos que controlam a serialização XML" e em "Atributos que controlam a serialização SOAP codificada" porque um serviço Web XML pode usar o estilo SOAP literal ou codificado. Para obter mais informações sobre como usar atributos para controlar o XML gerado por um serviço Web XML, consulte [Serialização XML com Serviços Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md). Para obter mais informações sobre serviços Web XML e SOAP, consulte [Personalizando mensagens SOAP](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx).  
  
## <a name="security-considerations-for-xmlserializer-applications"></a>Considerações de segurança para aplicativos XmlSerializer  
 Ao criar um aplicativo que use **XmlSerializer**, esteja ciente dos seguintes itens e de suas implicações:  
  
-   O **XmlSerializer** cria arquivos C# (.cs) e compila-os em arquivos .dll no diretório nomeado pela variável de ambiente TEMP; a serialização ocorre com essas DLLs.  
  
    > [!NOTE]
    >  Esses assemblies de serialização podem ser gerados com antecedência e assinados com o uso da ferramenta SGen.exe. Isso não funciona em um servidor de serviços Web. Em outras palavras, esses assemblies são apenas para uso de cliente e para serialização manual.  
  
     O código e as DLLs ficam vulneráveis a um processo mal-intencionado no momento de criação e compilação. Quando um computador que execute o Microsoft Windows NT 4.0 ou posterior é usado, é possível que dois ou mais usuários compartilhem o diretório TEMP. O compartilhamento de um diretório TEMP é perigoso quando as duas contas têm privilégios de segurança diferentes e a conta com maior privilégio executa um aplicativo usando o **XmlSerializer**. Nesse caso, um usuário pode violar a segurança do computador substituindo o arquivo .cs ou .dll compilado. Para eliminar essa preocupação, sempre verifique se cada conta no computador tem seu próprio perfil. Por padrão, as variáveis de ambiente TEMP apontam para um diretório diferente para cada conta.  
  
-   Se algum usuário mal-intencionado enviar um fluxo contínuo de dados XML para um servidor Web (um ataque de negação de serviço), então o **XmlSerializer** continuará a processar os dados até o computador ser executado com um número insuficiente de recursos.  
  
     Esse tipo de ataque será eliminado se você usar um computador que execute o IIS (Serviços de Informações da Internet) e seu aplicativo for executado no IIS. Os IIS apresenta um portão que não processa fluxos maiores do que uma quantidade especificada (o padrão é de 4 KB). Se você criar um aplicativo que não use o IIS e que desserialize com o **XmlSerializer**, você deverá implementar um portão similar que evite um ataque de negação de serviço.  
  
-   O **XmlSerializer** serializa dados e executa qualquer código usando qualquer tipo especificado para ele.  
  
     Existem duas maneiras de um objeto mal-intencionado apresentar uma ameaça. Ele pode executar o código mal-intencionado ou injetar o código mal-intencionado no arquivo C# criado pelo **XmlSerializer**. No primeiro caso, se um objeto mal-intencionado tentar executar um procedimento destrutivo, a segurança de acesso do código ajudará a evitar danos. No segundo caso, há uma possibilidade teórica de que um objeto mal-intencionado possa, de alguma forma, injetar o código no arquivo C# criado pelo **XmlSerializer**. Embora esse problema tenha sido examinado detalhadamente e um ataque desse tipo seja considerado improvável, é preciso tomar cuidado para nunca serializar dados com um tipo desconhecido e não confiável.  
  
-   Dados confidenciais serializados podem ficar vulneráveis.  
  
     Depois que o **XmlSerializer** serializar os dados, ele poderá ser armazenado como um arquivo XML ou como outro armazenamento de dados. Se seu repositório de dados estiver disponível para outros processos, ou estiver visível em uma intranet ou na Internet, os dados poderão ser roubados e usados de maneira mal-intencionada. Por exemplo, quando você cria um aplicativo que serializa pedidos que incluam números de cartão de crédito, os dados são altamente confidenciais. Para ajudar a evitar problemas, sempre proteja o repositório dos dados e siga as etapas para mantê-lo privado.  
  
## <a name="serialization-of-a-simple-class"></a>Serialização de uma classe simples  
 O exemplo de código a seguir mostra uma classe básica com um campo público.  
  
```vb  
Public Class OrderForm  
    Public OrderDate As DateTime  
End Class  
```  
  
```csharp  
public class OrderForm  
{  
    public DateTime OrderDate;  
}  
```  
  
 Quando uma instância dessa classe é serializada, ela pode ser similar ao exemplo a seguir.  
  
```xml  
<OrderForm>  
    <OrderDate>12/12/01</OrderDate>  
</OrderForm>  
```  
  
 Para obter mais exemplos de serialização, consulte [Exemplos de Serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="items-that-can-be-serialized"></a>Itens que podem ser serializados  
 Os itens a seguir podem ser serializados com a classe **XmLSerializer**:  
  
-   Propriedades e campos de leitura/gravação públicos de classes públicas.  
  
-   Classes que implementam **ICollection** ou **IEnumerable**.  
  
    > [!NOTE]
    >  Somente as coleções são serializadas, não propriedades públicas.  
  
-   Objetos **XmlElement**.  
  
-   Objetos **XmlNode**.  
  
-   Objetos **DataSet**.  
  
 Para obter mais informações sobre a serialização ou desserialização de objetos, consulte [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md) e [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md).  
  
## <a name="advantages-of-using-xml-serialization"></a>Vantagens de usar a serialização XML  
 A classe **XmlSerializer** confere controle total e flexível quando você serializa um objeto como XML. Se você estiver criando um serviço Web XML, poderá aplicar atributos que controlam a serialização para classes e membros para garantir que a saída XML esteja de acordo com um esquema específico.  
  
 Por exemplo, **XmlSerializer** permite que você:  
  
-   Especificar se um campo ou propriedade deve ser codificado como atributo ou como elemento.  
  
-   Especificar um namespace XML a ser usado.  
  
-   Especificar o nome de um elemento ou atributo se um nome de campo ou de propriedade estiver incorreto.  
  
 Outra vantagem da serialização XML é que não há restrições aos aplicativos que você desenvolve, contanto que o fluxo XML gerado esteja de acordo com o esquema especificado. Imagine um esquema usado para descrever livros. Ele apresenta os elementos título, autor, editor e número ISBN. Você pode desenvolver um aplicativo que processe os dados XML da forma que desejar, por exemplo, como um pedido de livro ou como um inventário de livros. Em ambos os casos, o único requisito é que o fluxo XML esteja de acordo com o esquema XSD especificado.  
  
## <a name="xml-serialization-considerations"></a>Considerações de serialização XML  
 A observação a seguir deve ser considerada ao usar a classe **XmlSerializer**:  
  
-   A ferramenta Sgen.exe é expressamente destinada a gerar assemblies de serialização para desempenho máximo.  
  
-   Os dados serializados contêm somente os próprios dados e a estrutura de suas classes. A identidade de tipos e as informações de assemblies não são incluídas.  
  
-   Somente as propriedades e os campos públicos podem ser serializados. As propriedades devem ter acessadores públicos (métodos get e set). Se você precisar serializar dados não públicos, use a classe <xref:System.Runtime.Serialization.DataContractSerializer>, em vez da serialização XML.  
  
-   Uma classe deve ter um construtor padrão a ser serializado por **XmlSerializer**.  
  
-   Os métodos não podem ser serializados.  
  
-   **XmlSerializer** pode processar classes que implementam **IEnumerable** ou **ICollection** de maneira diferente caso elas atendam a determinados requisitos, como a seguir.  
  
     Uma classe que implementa **IEnumerable** deve implementar um método **Add** público que aceita um único parâmetro. O parâmetro do método **Add** deve ser consistente (polimórfico) com o tipo retornado da propriedade **IEnumerator.Current**, retornada do método **GetEnumerator**.  
  
     Uma classe que implementa **ICollection**, além de **IEnumerable** (como **CollectionBase**), deve ter uma propriedade pública indexada **Item** (um indexador em C#) que aceite um inteiro e deve ter uma propriedade pública **Count** do tipo **integer**. O parâmetro passado para o método **Add** deve ser do mesmo tipo que aquele retornado pela propriedade **Item** ou deve corresponder a uma das bases desse tipo.  
  
     Para as classes que implementam **ICollection**, os valores a serem serializados são recuperados da propriedade indexada **Item**, não ao chamar **GetEnumerator**. Além disso, propriedades e campos públicos não são serializados, exceto os campos públicos que retornam outra classe de coleção (que implemente **ICollection**). Para obter um exemplo, consulte [Exemplos de serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="xsd-data-type-mapping"></a>Mapeamento de tipo de dados XSD  
 O documento "XML Schema Part 2: Datatypes" do World Wide Web Consortium (www.w3.org) especifica os tipos de dados simples que são permitidos em um esquema XSD. Para muitos desses tipos (por exemplo, **int** e **decimal**), há um tipo de dados correspondente no .NET Framework. No entanto, alguns tipos de dados XML não têm um tipo de dados correspondente no .NET Framework (por exemplo, o tipo de dados **NMTOKEN**). Nesses casos, se você usar a ferramenta de definição de esquema XML ([Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) para gerar classes de um esquema, um atributo apropriado será aplicado a um membro de tipo string e a respectiva propriedade **DataType** será definida como o nome do tipo de dados XML. Por exemplo, se um esquema contiver um elemento nomeado "MyToken" com o tipo de dados XML **NMTOKEN**, a classe gerada poderá conter um membro conforme mostrado no exemplo a seguir.  
  
```vb  
<XmlElement(DataType:="NMTOKEN")> _  
Public MyToken As String  
```  
  
```csharp  
[XmlElement(DataType = "NMTOKEN")]  
public string MyToken;  
```  
  
 Da mesma forma, se você estiver criando uma classe que precise estar em conformidade com um esquema XML (XSD) específico, deverá aplicar o atributo apropriado e definir sua propriedade **DataType** como o nome do tipo de dados XML desejado.  
  
 Para obter uma lista completa de mapeamentos de tipo, consulte a propriedade **DataType** para algumas das seguintes classes de atributos:  
  
-   <xref:System.Xml.Serialization.SoapAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.SoapElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlArrayItemAttribute>  
  
-   <xref:System.Xml.Serialization.XmlAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.XmlElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlRootAttribute>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Serialization.XmlSerializer>   
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.IO.FileStream>   
 [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)   
 [Serialização Binária](../../../docs/standard/serialization/binary-serialization.md)   
 [Serialização](../../../docs/standard/serialization/index.md)   
 <xref:System.Xml.Serialization.XmlSerializer>   
 [Exemplos de serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)   
 [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)   
 [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
