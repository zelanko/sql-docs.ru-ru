---
title: "Компонент потока данных во время выполнения методов | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: da14a10c936d1966e9317fe50141ecdb86c23379
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="run-time-methods-of-a-data-flow-component"></a>Методы времени выполнения для компонента потока данных
  Во время выполнения задача потока данных проверяет последовательность компонентов, подготавливает план выполнения и управляет пулом рабочих потоков, выполняющих план работы. Задача загружает строки данных из источников, обрабатывает их с помощью преобразований, а затем сохраняет в соответствующие назначения.  
  
## <a name="sequence-of-method-execution"></a>Последовательность выполнения методов  
 Во время выполнения компонента потока данных вызывается поднабор методов в базовом классе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Всегда вызываются одни и те же методы в одной и той же последовательности, за исключением методов <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. Эти два метода вызываются в зависимости от существования и конфигурации объектов <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> компонента.  
  
 Следующий список содержит методы в том порядке, в котором они вызываются во время выполнения компонента. Обратите внимание на то, что если метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> вызывается, это всегда происходит перед вызовом метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a>Метод PrimeOutput  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> вызывается, когда в компоненте имеется, по меньшей мере, один выход, присоединенный к нижестоящему компоненту через объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>, а свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> этого выхода имеет нулевое значение. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> вызывается для исходных компонентов и для преобразований с асинхронными выходами. В отличие от метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>, описываемого ниже, метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> вызывается только один раз для каждого компонента, где он требуется.  
  
### <a name="processinput-method"></a>Метод ProcessInput  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> вызывается для компонентов, имеющих, по меньшей мере, один вход, присоединенный к вышестоящему компоненту посредством объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> вызывается для целевых компонентов и для преобразований с синхронными выходами. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> вызывается повторно до тех пор, пока не будут обработаны все строки из вышестоящих компонентов.  
  
## <a name="working-with-inputs-and-outputs"></a>Работа с входами и выходами  
 Во время выполнения компонентами потока данных выполняются следующие задачи:  
  
-   Исходные компоненты добавляют строки.  
  
-   Компоненты преобразования с синхронными выходами получают строки, передаваемые исходными компонентами.  
  
-   Компоненты преобразования с асинхронными выходами получают строки и добавляют строки.  
  
-   Целевые компоненты получают строки и затем передают их в назначение.  
  
 Во время выполнения задача потока данных выделяет объекты <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, которые содержат все столбцы, определенные в коллекциях выходных столбцов последовательности компонентов. Например, если каждый из четырех компонентов в последовательности потока данных добавляет один выходной столбец в его коллекцию выходных столбцов, буфер, предоставляемый каждому компоненту, содержит четыре столбца, по одному для каждого выходного столбца на компонент. В силу этого компонент иногда получает буферы, содержащие столбцы, которые им не используются.  
  
 Поскольку буферы, которые получает компонент, могут содержать не используемые им столбцы, необходимо найти столбцы, которые должны быть использованы в коллекциях входных и выходных столбцов компонента, в буфере, предоставляемом компоненту задачей потока данных. Для этого используется метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>. Для улучшения производительности эта задача обычно выполняется во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, а не методов <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> или <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> вызывается перед методами <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> и является для компонента первой возможностью выполнить эту работу после получения компонентом доступа к <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>. Во время выполнения этого метода компоненту необходимо найти его столбцы в буферах и сохранить эти данные внутренне, чтобы столбцы можно было использовать в методах <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> или <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
 В следующем примере кода показано, как компонент преобразования с синхронным выходом осуществляет поиск своих входных столбцов в буфере во время выполнения <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a>Добавление строк  
 Компоненты предоставляют строки нижестоящим компонентам путем добавления строк в объекты <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>. Задача потока данных предоставляет массив выходных буферов, по одному для каждого объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>, соединенного с нижестоящим компонентом, в качестве параметра метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>. Исходные компоненты и компоненты преобразования с асинхронными выходами добавляют строки в буферы и вызывают метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> по окончании добавления строк. Задача потока данных управляет выходными буферами, предоставляемыми ею компонентам, и, по мере заполнения буфера, автоматически перемещает строки в буфере в следующий компонент. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> вызывается один раз для каждого компонента, в отличие от метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>, вызываемого неоднократно.  
  
 В следующем примере кода показано, как компонент добавляет строки в свои выходные буферы во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, а затем вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A>.  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 Дополнительные сведения о разработке компонентов, которые добавляют строки в выходные буферы см. в разделе [разработке пользовательского компонента источника](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) и [Разработка пользовательского компонента преобразования с асинхронными выходами](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).  
  
### <a name="receiving-rows"></a>Получение строк  
 Компоненты получают строки из вышестоящих компонентов в объектах <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>. Задача потока данных передает объект <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, который содержит строки, добавленные в поток данных вышестоящими компонентами, в качестве параметра метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. Этот входной буфер можно использовать для проверки и изменения строк и столбцов в буфере, но непригоден для добавления или удаления строк. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> вызывается повторно до тех пор, пока не останется ни одного доступного буфера. Вызывается, время последнего <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> свойство **true**. Можно просматривать коллекцию строк в буфере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A>, при этом буфер перемещается в следующую строку. Этот метод возвращает **false** когда буфер располагается в последней строке в коллекции. Нет необходимости проверять значение свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A>, если не требуется выполнить дополнительное действие после обработки последних строк данных.  
  
 Ниже показан правильный шаблон использования метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> и свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A>.  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 В следующем примере кода демонстрируется, как компонент обрабатывает строки во входных буферах во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 Дополнительные сведения о разработке компонентов, получающих строки во входные буферы см. в разделе [разработка компонентов назначения](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) и [Разработка пользовательского компонента преобразования с синхронными выходами](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="see-also"></a>См. также:  
 [Методы времени разработки компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md)  
  
  
