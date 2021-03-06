---
title: -target (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204510"
---
# <a name="-target-c-compiler-options"></a>-target (opções do compilador C#)
A opção de compilador **de destino** pode ser especificada em uma das quatro formas:  
  
 [-alvo:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Para criar um arquivo .exe para aplicativos windows 8.x Store.  
  
 [-alvo:exe](./target-exe-compiler-option.md)  
 Para criar um arquivo .exe.  
  
 [-alvo:biblioteca](./target-library-compiler-option.md)  
 Para criar uma biblioteca de códigos.  
  
 [-destino:módulo](./target-module-compiler-option.md)  
 Para criar um módulo.  
  
 [-alvo:winexe](./target-winexe-compiler-option.md)  
 Para criar um programa do Windows.  
  
 [-alvo:winmdobj](./target-winmdobj-compiler-option.md)  
 Para criar um arquivo .winmdobj intermediário.  
  
 A menos que você especifique **-target:module**, **-target** faz com que um manifesto de montagem .NET Framework seja colocado em um arquivo de saída. Para obter mais informações, consulte [Assembléias em .NET](../../../standard/assembly/index.md) e [Atributos Comuns](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 O manifesto do assembly é colocado no primeiro arquivo de saída .exe na compilação ou na primeira DLL, se não houver nenhum arquivo de saída .exe. Por exemplo, na linha de comando a seguir, o manifesto será colocado em `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 O compilador cria apenas um manifesto do assembly por compilação. As informações sobre todos os arquivos em uma compilação são colocados no manifesto do assembly. Todos os arquivos de saída, exceto os criados com **-target:module** podem conter um manifesto de montagem. Ao gerar vários arquivos de saída na linha de comando, apenas um manifesto do assembly pode ser criado e ele deve ir para o primeiro arquivo de saída especificado na linha de comando. Não importa qual é o primeiro arquivo de saída (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), todos os outros arquivos de saída produzidos na mesma compilação devem ser módulos (**-target:module**).  
  
 Se você criar um assembly, pode indicar que todo ou parte do seu código está em conformidade com CLS com o atributo <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Para obter mais informações sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Confira também

- [C# Opções de compilador](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (opções do compilador do C#)](./subsystemversion-compiler-option.md)
