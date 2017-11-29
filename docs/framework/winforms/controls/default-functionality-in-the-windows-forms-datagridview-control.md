---
title: "Funcionalidade padrão no controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d6b15085c301f074ef6fcf9e60a75299c4b245b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Funcionalidade padrão no controle DataGridView dos Windows Forms
Windows Forms <xref:System.Windows.Forms.DataGridView> controle fornece aos usuários uma quantidade significativa de funcionalidade padrão.  
  
## <a name="default-functionality"></a>Funcionalidade padrão  
 Por padrão, um <xref:System.Windows.Forms.DataGridView> controle:  
  
-   Exibe automaticamente os cabeçalhos de coluna e de linha que permanecem visíveis enquanto a tabela rola verticalmente.  
  
-   Tem um cabeçalho de linha que contém um indicador de seleção para a linha atual.  
  
-   Tem um retângulo de seleção na primeira célula.  
  
-   Tem colunas que podem ser redimensionadas automaticamente quando o usuário clicar duas vezes nos divisores de coluna.  
  
-   Suporta automaticamente estilos visuais no Windows XP e a família Windows Server 2003 quando o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método é chamado a partir do aplicativo `Main` método.  
  
 Além disso, o conteúdo de um <xref:System.Windows.Forms.DataGridView> controle pode ser editado por padrão:  
  
-   Se o usuário clica duas vezes ou pressiona F2 em uma célula, o controle automaticamente coloca a célula no modo de edição e atualiza o conteúdo da célula à medida que o usuário digita.  
  
-   Se o usuário rolar até o final da grade, o usuário verá que existe uma linha para adicionar novos registros. Quando o usuário clica essa linha, uma nova linha é adicionada para o <xref:System.Windows.Forms.DataGridView> controle com valores padrão. Quando o usuário pressiona ESC, essa nova linha desaparece.  
  
-   Se o usuário clicar em um cabeçalho de linha, a linha inteira será selecionada.  
  
 Quando você associa um <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados definindo sua <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade, o controle:  
  
-   Usa automaticamente os nomes das colunas da fonte de dados como o texto do cabeçalho de coluna.  
  
-   É populado com o conteúdo da fonte de dados. <xref:System.Windows.Forms.DataGridView>colunas são criadas automaticamente para cada coluna na fonte de dados.  
  
-   Cria uma linha para cada linha visível na tabela.  
  
-   Classifica automaticamente as linhas com base nos dados subjacentes quando o usuário clica em um cabeçalho de coluna.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)