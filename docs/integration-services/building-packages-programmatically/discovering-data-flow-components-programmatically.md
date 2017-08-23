---
title: "Поиск компонентов потока данных программными средствами | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 78090618d5025a6ab29c888d09db44ddfff278fa
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="discovering-data-flow-components-programmatically"></a>Программный поиск компонентов потока данных
  После добавления задачи потока данных в пакет может возникнуть необходимость определить, какие компоненты потока данных доступны для использования. Можно программным способом выявить источники, преобразования и назначения потока данных, установленные и доступные на локальном компьютере. Сведения о добавлении к пакету задачу потока данных см. в разделе [данных потока задач программное добавление](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md).  
  
## <a name="discovering-components"></a>Поиск компонентов  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> предоставляет коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A>, содержащую объект <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> для каждого компонента, правильно установленного на локальном компьютере. Каждый объект <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> содержит сведения о компоненте, в частности, его имя, описание и время создания. Можно использовать значение, возвращаемое в свойстве <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A>, чтобы задать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> при добавлении компонента в пакет.  
  
## <a name="next-step"></a>Следующий шаг  
 После выявления доступных компонентов, следующим шагом является добавление и настройка компонентов, который рассматривается в следующем разделе [Добавление данных потока компонентов программным образом](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md).  
  
## <a name="sample"></a>Образец  
 В следующем образце кода показано, как перечислить коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> объекта <xref:Microsoft.SqlServer.Dts.Runtime.Application>, чтобы программным способом определить компоненты потока данных, доступные на локальном компьютере. В этом примере требуется ссылка на сборку Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```
  
## <a name="see-also"></a>См. также:  
 [Добавление компонентов потока данных программными средствами](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
