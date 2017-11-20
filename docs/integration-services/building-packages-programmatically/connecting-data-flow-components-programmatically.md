---
title: "Соединение компонентов потока данных программными средствами | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
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
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 40869328965e049b5981e94655226bc0a78dc37f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-data-flow-components-programmatically"></a>Программное соединение компонентов потока данных
  После добавления компонентов в задачу потока данных их следует соединить, чтобы создать дерево выполнения, представляющее поток данных из источников через преобразования в назначения. Объекты <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> используются для соединения компонентов в потоке данных.  
  
## <a name="creating-a-path"></a>Создание пути  
 Новый метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> интерфейс для создания нового пути и добавить его в коллекцию путей задачи потока данных. Этот метод возвращает новый, неподсоединенный объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>, который можно затем использовать для соединения двух компонентов.  
  
 Вызовите метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> для подключения к пути и уведомления компонентов, участвующих в пути, что они были соединены. Этот метод принимает в качестве параметров объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> вышестоящего компонента и объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> компонента, расположенного ниже по потоку данных. По умолчанию при обращении к методу <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> этого компонента создается единственный вход для компонентов, имеющих входы, и единственный выход для компонентов, имеющих выходы. Следующий пример использует выход источника по умолчанию и вход назначения.  
  
## <a name="next-step"></a>Следующий шаг  
 После установления пути между двумя компонентами следующий шаг — для сопоставления входных столбцов в нижестоящего компонента, который рассматривается в следующем разделе [Выбор входных столбцов программным образом](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md).  
  
## <a name="sample"></a>Образец  
 Следующий образец кода показывает, как установить путь между двумя компонентами.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 }  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор входных столбцов программным способом](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  

