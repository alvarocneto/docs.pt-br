---
title: Esquema de configurações do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844222"
---
# <a name="application-settings-schema"></a>Esquema de configurações do aplicativo

As configurações de aplicativo permitem que um aplicativo Windows Forms ou do ASP.NET armazene e recupere configurações no escopo do aplicativo e no escopo do usuário. Nesse contexto, uma *configuração* é qualquer informação que podem ser específicos do usuário atual ou específica do aplicativo — qualquer coisa, desde uma cadeia de caracteres de conexão de banco de dados para o usuário preferencial tamanho de janela padrão do.

Por padrão, as configurações do aplicativo em um aplicativo Windows Forms usa o <xref:System.Configuration.LocalFileSettingsProvider> classe, que usa o sistema de configuração do .NET para armazenar configurações em um arquivo de configuração XML. Para obter mais informações sobre os arquivos usados pelas configurações de aplicativo, consulte [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).

As configurações de aplicativo define os elementos a seguir como parte dos arquivos de configuração, ele usa.

| Elemento                    | Descrição                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Contém todos os  **\<Configuração >** marcas específicas para o aplicativo.                         |
| **\<userSettings >**        | Contém todos os  **\<Configuração >** marcas específicas para o usuário atual.                        |
| **\<Configuração >**             | Define uma configuração. Filho de um  **\<applicationSettings >** ou  **\<userSettings >**. |
| **\<value>**               | Define um valor de configuração. Filho de  **\<Configuração >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > elemento

Esse elemento contém todos os  **\<Configuração >** marcas que são específicas a uma instância do aplicativo em um computador cliente. Não define nenhum atributo.

## <a name="usersettings-element"></a>\<userSettings > elemento

Esse elemento contém todos os  **\<Configuração >** marcas que são específicas para o usuário que está usando atualmente o aplicativo. Não define nenhum atributo.

## <a name="setting-element"></a>\<Configuração > elemento

Esse elemento define uma configuração. Ele tem os seguintes atributos.

| Atributo        | Descrição |
| ---------------- | ----------- |
| **name**         | Necessário. A ID exclusiva da configuração. As configurações criadas por meio do Visual Studio são salvos com o nome `ProjectName.Properties.Settings`. |
| **serializedAs** | Necessário. O formato a ser usado para serializar o valor em texto. Os valores válidos são:<br><br>- `string`. O valor é serializado como uma cadeia de caracteres usando um <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. O valor é serializado usando a serialização de XML.<br>- `binary`. O valor é serializado como texto codificado binário usando a serialização binária.<br />- `custom`. O provedor de configurações possui conhecimento inerente dessa configuração e serializa e desserializa-o. |

## <a name="value-element"></a>\<valor > elemento

Esse elemento contém o valor de uma configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um arquivo de configurações do aplicativo que define duas configurações no escopo do aplicativo e duas configurações de escopo do usuário:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Consulte também

[Visão geral sobre configurações de aplicativo](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Arquitetura das Configurações do Aplicativo](~/docs/framework/winforms/advanced/application-settings-architecture.md)
