---
title: 'Como: converter uma imagem BMP em uma imagem PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 59200941aa0f872a0bd99510bfaa8a8b878a9061
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648298"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Como: converter uma imagem BMP em uma imagem PNG
Muitas vezes, convém converter do formato de arquivo de uma imagem para outra. Você pode fazer essa conversão facilmente por meio da chamada a <xref:System.Drawing.Image.Save%2A> método da <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo de imagem desejada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um aplicativo Windows Forms.  
  
- Uma referência para o `System.Drawing.Imaging` namespace.  
  
## <a name="see-also"></a>Consulte também

- [Como: Listar os codificadores instalados](how-to-list-installed-encoders.md)
- [Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado](using-image-encoders-and-decoders-in-managed-gdi.md)
- [Tipos de Bitmaps](types-of-bitmaps.md)
