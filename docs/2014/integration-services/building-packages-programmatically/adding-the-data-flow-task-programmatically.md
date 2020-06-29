---
title: Добавление задачи потока данных программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9291673fec31064befed704560e96693c3641d7c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439291"
---
# <a name="adding-the-data-flow-task-programmatically"></a>Добавление задачи потока данных программным образом
  Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] включает задачу потока данных, представленную пространством имен <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> в объектной модели. Задача потока данных — это специализированная высокопроизводительная задача, предназначенная для преобразования и перемещения данных во время выполнения пакета. Как и другие задачи, задача потока данных упакована в объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, и с точки зрения подсистемы выполнения эта задача является просто одной из задач в пакете. Однако поток данных содержит дополнительные объекты, называемые компонентами потока данных. Эти компоненты выполняют перемещение данных из источника в место назначения, иногда посредством преобразования. Эти компоненты определяют направление перемещения и способ преобразования данных. Настройка задачи потока данных включает добавление компонентов в задачу, а затем их соединение для установления потока данных и выполнения требуемого преобразования.  
  
 В задаче потока данных имеются компоненты трех типов: **Источники потока данных**, **Преобразования потока данных** и **Назначения потока данных**, которые отображаются в этом порядке на панели элементов конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Эти типы также называются просто источниками, преобразованиями и назначениями. Как видно из имен, поток данных направляется из источника в компонент преобразования, а затем назначению. Это простое описание потока данных, иллюстрирующее понятие, но задача потока данных является достаточно гибкой и мощной для обработки нескольких источников и объединения нескольких преобразований, отправляющих выходные данные нескольким назначениям.  
  
 Задача потока данных добавляется в пакет так же, как и другие задачи. После добавления задачи она настраивается путем добавления компонентов в задачу потока данных, настройки и соединения компонентов в задаче.  
  
## <a name="sample"></a>Образец  
 В следующем образце кода показан способ добавления задачи потока данных в пакет. Этот пример требует наличия ссылок на сборки Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap и Microsoft.SqlServer.ManagedDTS.  
  
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
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [EzAPI — обновление для SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) на сайте blogs.msdn.com.  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Программный поиск компонентов потока данных](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
