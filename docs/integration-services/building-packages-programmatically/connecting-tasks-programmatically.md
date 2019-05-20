---
title: Соединение задач программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9d5e7e6cdb7dc5cc50d292ef0b6b0e39b176e837
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65729300"
---
# <a name="connecting-tasks-programmatically"></a>Соединение задач программным образом

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Управление очередностью, представленное в объектной модели классом <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, устанавливает порядок запуска объектов <xref:Microsoft.SqlServer.Dts.Runtime.Executable> в пакете. Управление очередностью позволяет установить зависимость выполнения контейнеров и задач в пакете от результата выполнения предыдущего контейнера или задачи. Элементы управления очередностью устанавливаются между парами объектов <xref:Microsoft.SqlServer.Dts.Runtime.Executable> путем вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> объекта-контейнера. После создания ограничения между двумя исполняемыми объектами необходимо задать значение свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>, устанавливающего критерии выполнения второго исполняемого объекта, определенного в ограничении.  
  
 В зависимости от значения, заданного свойству <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A>, можно использовать одновременно и ограничение, и выражение в одном и том же управлении очередностью, как описано в следующей таблице.  
  
|Значение свойства EvalOp|Описание|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|Указывает, что результат выполнения определяет, будет ли запущен связанный ограничением контейнер или задача. Задайте свойству <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> необходимое значение из перечисления <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|Указывает, что значение выражения определяет, будет ли запущен связанный ограничением контейнер или задача. Задайте значение свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|Указывает, что связанный ограничением контейнер или задача будут выполнены, если выполнится ограничение и выражение вернет положительный результат. Установите свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, а свойство <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> установите в значение **true**.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|Указывает, что связанный ограничением контейнер или задача будут выполнены, если выполнится ограничение либо выражение вернет положительный результат. Установите свойства <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, а свойство <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> установите в значение **false**.|  
  
 Следующий образец кода демонстрирует добавление двух задач в пакет. Между ними создается управление очередностью <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, препятствующее выполнению второй задачи до завершения первой.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```
  
## <a name="see-also"></a>См. также:  
 [Добавление задачи потока данных программным образом](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
