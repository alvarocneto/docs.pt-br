---
title: Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: adee6ab283fb7e2fe9bbfcda78c9692621407e9e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089890"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer
O <xref:System.Windows.Forms.DataGridView> controle permite especificar estilos de célula padrão e formatos de dados para todo o controle, para colunas específicas, para os cabeçalhos de linha e coluna e para linhas para criar um efeito de razão alternadas de célula. Os estilos padrão definidos para todo o controle serão substituídos por estilos padrão definidos para colunas e linhas alternadas. Além disso, os estilos definidos no código para as linhas e células individuais substituem os estilos padrão.  
  
 Para obter mais informações sobre estilos de célula, consulte [Estilos de Célula no Controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Para definir estilos para linhas alternadas, consulte [Como Definir Estilos de Linha Alternada para o Controle DataGridView dos Windows Forms Usando o Designer](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Você também pode definir estilos usando o <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade afete todas as linhas que serão adicionadas ao controle. Para obter mais informações sobre o modelo de linha, consulte [Como Usar o Modelo de Linha para Personalizar Linhas no Controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Definir estilos padrão para todas as células no controle  
  
1.  Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.  
  
2.  No **propriedades** janela, clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) lado a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> propriedade. A caixa de diálogo **Criador de CellStyle** aparecerá.  
  
3.  Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.  
  
> [!NOTE]
>  Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna (exceto para o <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) serão automaticamente estilizados pelo tema atual, substituindo o <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> valores de propriedade.  
>   
>  Você pode definir estilos de célula para seleção múltipla <xref:System.Windows.Forms.DataGridView> controla usando o designer, mas somente se elas tiverem valores idênticos para a propriedade de estilo de célula que você deseja modificar. Caso algum estilo de célula seja diferente nessa propriedade, a janela **Propriedades** da caixa de diálogo **Criador de CellStyle** ficará em branco.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Definir estilos padrão para células em colunas individuais  
  
1.  Clique com botão direito do <xref:System.Windows.Forms.DataGridView> no designer de controle e escolha **Edit Columns**.  
  
2.  Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3.  No **propriedades da coluna** grade, clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) lado a <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade. A caixa de diálogo **Criador de CellStyle** aparecerá.  
  
4.  Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.  
  
### <a name="to-format-data-in-cells"></a>Formatar dados em células  
  
1.  Use um dos procedimentos anteriores para exibir uma caixa de diálogo **Criador de CellStyle** relacionada a uma propriedade de estilo de célula padrão.  
  
2.  No **construtor CellStyle** caixa de diálogo, clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) lado a <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade. A caixa de diálogo **Editar Cadeia de Caracteres** será exibida.  
  
3.  Selecione um tipo de formato e, em seguida, modifique os detalhes do tipo (como o número de casas decimais a serem exibidas), usando a caixa **Exemplo** para confirmar suas escolhas.  
  
4.  Se você estiver associando a <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados que é provável que contenham valores nulos, preencha o **valor nulo** caixa de texto. Esse valor é exibido quando o valor da célula for igual a uma referência nula (`Nothing` no Visual Basic) ou <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Como definir estilos de linhas alternados para o controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [Como: criar um projeto de aplicativo do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
