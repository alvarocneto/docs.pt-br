---
title: Como girar um objeto usando um caminho geométrico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 6d6d21f3f7b609cb2933093a6990425deb39d4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398142"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Como girar um objeto usando um caminho geométrico
Este exemplo mostra como girar um objeto ao longo de um caminho geométrico que é definido por um <xref:System.Windows.Media.PathGeometry> objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa três <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico.  
  
-   A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima um <xref:System.Windows.Media.RotateTransform> que é aplicado ao retângulo. A animação gera valores de ângulos. Isso faz o retângulo girar ao longo dos contornos do caminho.  
  
-   Os dois objetos animam os <xref:System.Windows.Media.TranslateTransform.X%2A> e <xref:System.Windows.Media.TranslateTransform.Y%2A> valores de um <xref:System.Windows.Media.TranslateTransform> que é aplicado ao retângulo. Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Outra maneira de girar um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do objeto e defina sua <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade `true`. Para obter mais informações e um exemplo, consulte [girar um objeto usando um caminho Geométrico (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
