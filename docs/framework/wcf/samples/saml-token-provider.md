---
title: Fornecedor de token SAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc6eaa916507c7e1c530d4ee757097bf0bffcd34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="saml-token-provider"></a>Fornecedor de token SAML
Este exemplo demonstra como implementar um provedor de token SAML de cliente personalizadas. Um provedor de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para fornecer credenciais para a infraestrutura de segurança. O provedor de token em geral examina o destino e problemas apropriada credenciais para que a infraestrutura de segurança possa proteger a mensagem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é fornecido com o provedor de Token do Gerenciador de credenciais padrão. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também é fornecida com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token. Provedores de token personalizados são úteis nos seguintes casos:  
  
-   Se você tiver um repositório de credenciais que esses provedores de token não podem operar com.  
  
-   Se desejar fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente usa as credenciais.  
  
-   Se você estiver criando um token personalizado.  
  
 Este exemplo mostra como criar um provedor de token personalizado que permite que um token SAML obtido fora do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente a ser usado.  
  
 Para resumir, este exemplo demonstra o seguinte:  
  
-   Como um cliente pode ser configurado com um provedor do token.  
  
-   Como um token SAML pode ser passado para as credenciais de cliente personalizadas.  
  
-   Como o token SAML é fornecido para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente.  
  
-   Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.  
  
 O serviço expõe dois pontos de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. Cada ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão `wsFederationHttpBinding`, que usa segurança de mensagem. Um ponto de extremidade espera que o cliente para autenticar com um token SAML que usa uma chave de prova simétrica enquanto o outro espera que o cliente para autenticar com um token SAML que usa uma chave assimétrica de prova. O serviço também configura o certificado de serviço usando `serviceCredentials` comportamento. O `serviceCredentials` comportamento permite que você configure um certificado de serviço. Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem. A configuração a seguir faz referência ao certificado de "localhost" instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação no final deste tópico. O `serviceCredentials` comportamento também permite que você configure os certificados que são confiáveis para autenticar os tokens SAML. A configuração a seguir faz referência ao certificado de 'Alice' instalado durante a amostragem.  
  
```xml  
<system.serviceModel>  
 <services>  
  <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
   <host>  
    <baseAddresses>  
     <!-- configure base address provided by host -->  
     <add    
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />  
    </baseAddresses>  
   </host>  
   <!-- use base address provided by host -->  
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->  
   <endpoint address="calc/symm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->  
   <endpoint address="calc/asymm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding2"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
 </services>  
  
 <bindings>  
  <wsFederationHttpBinding>  
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->  
   <binding name="Binding1">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"   
              issuedKeyType="SymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>  
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->  
   <binding name="Binding2">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"  
              issuedKeyType="AsymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>          
  </wsFederationHttpBinding>  
 </bindings>  
  
 <behaviors>  
  <serviceBehaviors>  
   <behavior name="CalculatorServiceBehavior">  
    <!--   
    The serviceCredentials behavior allows one to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
    <serviceCredentials>  
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->  
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >  
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->  
      <knownCertificates>  
       <add storeLocation="LocalMachine"   
            storeName="TrustedPeople"   
            x509FindType="FindBySubjectName"   
            findValue="Alice"/>  
      </knownCertificates>  
     </issuedTokenAuthentication>  
     <serviceCertificate storeLocation="LocalMachine"  
                         storeName="My"  
                         x509FindType="FindBySubjectName"  
                         findValue="localhost"  />  
    </serviceCredentials>  
   </behavior>  
  </serviceBehaviors>  
 </behaviors>  
  
</system.serviceModel>  
```  
  
 As etapas a seguir mostram como desenvolver um provedor do token SAML e integrá-lo ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: estrutura de segurança:  
  
1.  Grave um provedor do token SAML.  
  
     O exemplo implementa um provedor de token de SAML personalizado que retorna um token de segurança com base em uma asserção SAML que é fornecida no tempo de construção.  
  
     Para executar essa tarefa, o provedor do token é derivado do <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substituições de <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método. Esse método cria e retorna um novo `SecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
     // Create a SamlSecurityToken from the provided assertion  
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);  
  
     // Create a SecurityTokenSerializer that will be used to   
     // serialize the SamlSecurityToken  
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();  
     // Create a memory stream to write the serialized token into  
     // Use an initial size of 64Kb  
     MemoryStream s = new MemoryStream(UInt16.MaxValue);  
  
     // Create an XmlWriter over the stream  
     XmlWriter xw = XmlWriter.Create(s);  
  
     // Write the SamlSecurityToken into the stream  
     ser.WriteToken(xw, samlToken);  
  
     // Seek back to the beginning of the stream  
     s.Seek(0, SeekOrigin.Begin);  
  
     // Load the serialized token into a DOM  
     XmlDocument dom = new XmlDocument();  
     dom.Load(s);  
  
     // Create a KeyIdentifierClause for the SamlSecurityToken  
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();  
  
    // Return a GenericXmlToken from the XML for the   
    // SamlSecurityToken, the proof token, the valid from and valid  
    // until times from the assertion and the key identifier clause  
    // created above  
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);  
    }  
    ```  
  
2.  Grave o Gerenciador de token de segurança personalizada.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe é usada para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método. Um Gerenciador de token de segurança também é usado para criar o serializador de token e autenticadores de token, mas aqueles não são cobertas por este exemplo. Neste exemplo de segurança personalizada herda do Gerenciador de token o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenProvider` método para retornar o provedor do token SAML quando os requisitos de token passados indicam que o token SAML é solicitado. Se a classe de credenciais de cliente (consulte a etapa 3) não tiver especificado uma asserção, o Gerenciador de token de segurança cria uma instância apropriada.  
  
    ```  
    public class SamlSecurityTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
     SamlClientCredentials samlClientCredentials;  
  
     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)  
      : base(samlClientCredentials)  
     {  
      // Store the creating client credentials  
      this.samlClientCredentials = samlClientCredentials;  
     }  
  
     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
     {  
      // If token requirement matches SAML token return the   
      // custom SAML token provider  
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||  
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")  
      {  
       // Retrieve the SAML assertion and proof token from the   
       // client credentials  
       SamlAssertion assertion = this.samlClientCredentials.Assertion;  
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;  
  
       // If either the assertion of proof token is null...  
       if (assertion == null || prooftoken == null)  
       {  
        // ...get the SecurityBindingElement and then the   
        // specified algorithm suite  
        SecurityBindingElement sbe = null;  
        SecurityAlgorithmSuite sas = null;  
  
        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))  
        {  
         sas = sbe.DefaultAlgorithmSuite;  
        }  
  
        // If the token requirement is for a SymmetricKey based token..  
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)  
        {  
         // Create a symmetric proof token  
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );  
         // and a corresponding assertion based on the claims specified in the client credentials  
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);  
        }  
        // otherwise...  
        else  
        {  
         // Create an asymmetric proof token  
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();  
         // and a corresponding assertion based on the claims   
         // specified in the client credentials  
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );  
        }  
       }  
  
       // Create a SamlSecurityTokenProvider based on the assertion and proof token  
       return new SamlSecurityTokenProvider(assertion, prooftoken);  
      }  
      // otherwise use base implementation  
      else  
      {  
       return base.CreateSecurityTokenProvider(tokenRequirement);  
      }  
    }  
    ```  
  
3.  Grave uma credencial de cliente personalizadas.  
  
     Classe de credenciais de cliente é usado para representar as credenciais que são configuradas para o proxy de cliente e cria o Gerenciador de token que é usado para obter o serializador de token, provedores de token e autenticadores de token de segurança.  
  
    ```  
    public class SamlClientCredentials : ClientCredentials  
    {  
     ClaimSet claims;  
     SamlAssertion assertion;  
     SecurityToken proofToken;  
  
     public SamlClientCredentials() : base()  
     {  
      // Set SupportInteractive to false to suppress Cardspace UI  
      base.SupportInteractive = false;  
     }  
  
     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )  
     {  
      // Just do reference copy given sample nature  
      this.assertion = other.assertion;  
      this.claims = other.claims;  
      this.proofToken = other.proofToken;  
     }  
  
     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }  
  
     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }  
     public ClaimSet Claims { get { return claims; } set { claims = value; } }  
  
     protected override ClientCredentials CloneCore()  
     {  
      return new SamlClientCredentials(this);  
     }  
  
     public override SecurityTokenManager CreateSecurityTokenManager()  
     {  
      // return custom security token manager  
      return new SamlSecurityTokenManager(this);  
     }  
    }  
    ```  
  
4.  Configure o cliente para usar a credencial de cliente personalizadas.  
  
     O exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente para que o cliente pode usar a credencial de cliente personalizadas.  
  
    ```  
    // Create new credentials class  
    SamlClientCredentials samlCC = new SamlClientCredentials();  
  
    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case  
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");  
  
    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case  
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");  
  
    // Create some claims to put in the SAML assertion  
    IList<Claim> claims = new List<Claim>();  
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));  
    ClaimSet claimset = new DefaultClaimSet(claims);  
    samlCC.Claims = claimset;  
  
    // set new credentials  
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);  
    ```  
  
 Sobre o serviço, as declarações associadas ao chamador são exibidas. Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
## <a name="setup-batch-file"></a>Arquivo de lote  
 Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com o certificado apropriado para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.  
  
-   Criando o certificado do servidor:  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O valor padrão, esse arquivo em lotes é localhost.  
  
     O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:  
  
     Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Criando o certificado do emissor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do emissor a ser usado. O `%USER_NAME%` variável Especifica o nome do emissor. Altere essa variável para especificar seu próprio nome de emissor. O valor padrão, esse arquivo em lotes é Alice.  
  
     O certificado é armazenado no meu repositório no local de armazenamento CurrentUser.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do emissor no repositório de certificados confiáveis do servidor.  
  
     Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados do servidor com o certificado do emissor não é necessária.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
> [!NOTE]
>  Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando executado com privilégios de administrador. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.  
  
2.  Inicie Service.exe de service\bin.  
  
3.  Inicie Client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador de serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço. Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
3.  Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador. O arquivo Service.exe.config deve ser atualizado para refletir o novo nome de certificado. Você pode criar o certificado do servidor, modificando o arquivo em lotes bat. Observe que o arquivo bat deve ser executado em uma janela de prompt de comando do Visual Studio aberta com privilégios de administrador. Você deve definir o `%SERVER_NAME%` variável para o nome de host totalmente qualificado do computador que é usado para hospedar o serviço.  
  
4.  Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople do cliente. Essa etapa não é necessária quando o certificado do servidor é emitido por um emissor confiável do cliente.  
  
5.  No arquivo Service.exe.config no computador de serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.  
  
6.  No computador do serviço, execute Service.exe em um prompt de comando.  
  
7.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No computador cliente, inicie o `Client.exe` em uma janela de prompt de comando.  
  
10. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
## <a name="see-also"></a>Consulte também