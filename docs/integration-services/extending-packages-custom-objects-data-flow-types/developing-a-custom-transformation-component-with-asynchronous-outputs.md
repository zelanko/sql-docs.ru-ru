---
title: Разработка пользовательского компонента преобразования с асинхронными выходами | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], transformation components
- asynchronous outputs [Integration Services]
- ProcessInput method
- cache [Integration Services]
- buffer allocations [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], transformation components
ms.assetid: 1c3e92c7-a4fa-4fdd-b9ca-ac3069536274
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e1d5cde6cef1d6ce53d29fb04f330aa2c06c1c8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71287925"
---
# <a name="developing-a-custom-transformation-component-with-asynchronous-outputs"></a>Разработка пользовательского компонента преобразования с асинхронными выходами

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Если преобразование не может вывести строки до того, как компонент получит все входные строки, или может создавать несколько выходных строк на одну входную, нужно использовать компонент с асинхронным выходом. Например, преобразование «Статистическая обработка» не может вычислить суммарное значение для всех строк, пока не считает все строки. Напротив, компонент с синхронными выходами можно использовать в случае, если каждая строка преобразуется, проходя через этот компонент. Можно изменять данные каждой строки на месте или добавлять к строке один или несколько новых столбцов, каждый из которых содержит значение для каждого входного ряда. Дополнительные сведения о различиях между синхронными и асинхронными компонентами см. в разделе [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Компоненты преобразования с асинхронными выходами уникальны, поскольку выступают одновременно в роли компонента-источника и целевого компонента. Такой компонент получает строки от вышестоящих компонентов и добавляет строки, получаемые нижестоящими компонентами. Никакой другой компонент потока данных не выполняет обе операции сразу.  
  
 Столбцы, полученные от вышестоящих компонентов и доступные компоненту с синхронными выходами, автоматически становятся доступны компонентам, нижестоящим по отношению к данному компоненту. Поэтому компоненту с синхронными выходами не нужно определять выходные столбцы, чтобы обеспечить следующему компоненту столбцы и строки. С другой стороны, компоненту с асинхронными выходами нужно определять выходные столбцы и предоставлять строки нижестоящим компонентам. Следовательно, компоненту с асинхронными выходами приходится выполнять больше задач, как во время разработки, так и во время выполнения, а разработчику этого компонента приходится писать больше кода.  
  
 Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат несколько преобразований с асинхронными выходами. Например, преобразование «Сортировка» требует получения всех строк до того, как их можно будет сортировать, и использует для этого асинхронные выходы. После получения всех строк преобразование сортирует их и добавляет к выходу.  
  
 В данном разделе приводится подробное описание разработок преобразований с асинхронными выходами. Дополнительные сведения о разработке компонентов-источников см. в разделе [Разработка пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).  
  
## <a name="design-time"></a>Время разработки  
  
### <a name="creating-the-component"></a>Создание компонента  
 Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> определяет, является ли его выход синхронным или асинхронным. Для создания асинхронного выхода добавьте выход к компоненту и задайте для свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> значение 0. Значение этого свойства определяет также, выделяет ли задача потока данных объекты <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> для входа и выхода данного компонента или же выделяется один буфер, используемый обоими объектами сразу.  
  
 Далее приводится образец кода, создающий асинхронный выход в реализации метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>.  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "AsyncComponent",ComponentType = ComponentType.Transform)]  
    public class AsyncComponent : PipelineComponent  
    {  
        public override void ProvideComponentProperties()  
        {  
            // Call the base class, which adds a synchronous input  
            // and output.  
            base.ProvideComponentProperties();  
  
            // Make the output asynchronous.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
            output.SynchronousInputID = 0;  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="AsyncComponent", ComponentType:=ComponentType.Transform)> _  
Public Class AsyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Call the base class, which adds a synchronous input  
        ' and output.  
        Me.ProvideComponentProperties()  
  
        ' Make the output asynchronous.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
        output.SynchronousInputID = 0  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a>Создание и настройка выходных столбцов  
 Как уже упоминалось, асинхронный компонент добавляет столбцы к своей коллекции выходных столбцов, чтобы предоставить столбцы нижележащим компонентам. Существует несколько методов времени разработки, которые можно использовать в зависимости от потребностей компонента. Например, для передачи всех столбцов из вышестоящих компонентов нижестоящим нужно переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> для добавления столбцов, поскольку это первый метод, в котором входные столбцы становятся доступны компоненту.  
  
 Если компонент создает выходные столбцы на основе столбцов, выбранных для входа, нужно переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A>, чтобы он выбирал выходные столбцы и указывал, как они должны использоваться.  
  
 Если компонент с асинхронными выходами создает выходные столбцы на основе столбцов, полученных от вышестоящих компонентов, и все доступные вышестоящие столбцы изменяются, компоненту следует изменять свою собственную коллекцию выходных столбцов. Эти изменения должны обнаруживаться компонентом во время работы метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> и исправляться при вызове метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.  
  
> [!NOTE]  
>  Если выходной столбец удалить из коллекции выходных столбцов, это негативно повлияет на использующие его нижележащие компоненты потока данных. Выходной столбец нужно исправить, а не удалять и не создавать заново, чтобы не нарушить работы нижестоящих компонентов. Например, если тип данных столбца изменился, нужно обновить тип данных.  
  
 В следующем примере кода показан компонент, добавляющий столбец в коллекцию выходных столбцов, по одному на каждый столбец, получаемый от вышестоящего компонента.  
  
```csharp  
public override void OnInputPathAttached(int inputID)  
{  
   IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
   IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
   IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
   foreach (IDTSVirtualInputColumn100 vCol in vInput.VirtualInputColumnCollection)  
   {  
      IDTSOutputColumn100 outCol = output.OutputColumnCollection.New();  
      outCol.Name = vCol.Name;  
      outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage);  
   }  
}  
```  
  
```vb  
Public Overrides Sub OnInputPathAttached(ByVal inputID As Integer)  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
    Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput()  
  
    For Each vCol As IDTSVirtualInputColumn100 In vInput.VirtualInputColumnCollection  
  
        Dim outCol As IDTSOutputColumn100 = output.OutputColumnCollection.New()  
        outCol.Name = vCol.Name  
        outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage)  
  
    Next  
End Sub  
```  
  
## <a name="run-time"></a>Время выполнения  
 Компоненты с асинхронным выходом также исполняют методы в последовательности, отличной от других типов компонентов, во время выполнения. Во-первых, это единственные компоненты, в которых вызываются оба метода: <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. Компоненты с асинхронным выходом также требуют доступа ко всем входящим строкам, прежде чем смогут начать обработку; поэтому они должны сохранять входные строки в своем внутреннем кэше, пока все строки не будут прочитаны. И наконец, в отличие от других компонентов, компоненты с асинхронным выходом получают и входной, и выходной буфер.  
  
### <a name="understanding-the-buffers"></a>Основные сведения о буферах  
 Компонент получает входной буфер при вызове метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. Этот буфер содержит строки, добавленные туда вышестоящими компонентами. Буфер также содержит столбцы входа компонента, помимо столбцов, предоставленных в качестве выхода вышестоящего компонента, но не добавленных к входной коллекции асинхронного компонента.  
  
 Выходной буфер, предоставленный компоненту в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, вначале не содержит строк. Компонент добавляет строки к этому буферу и, когда буфер заполнится, предоставляет его нижестоящим компонентам. Выходной буфер содержит столбцы, определенные в коллекции выходных столбцов компонента, помимо столбцов, добавленных к выводам других нижестоящих компонентов.  
  
 Не так ведут себя компоненты с синхронными выходами — они получают единый буфер с общим доступом. Общий буфер компонента с синхронными выходами содержит и входные, и выходные столбцы компонента, помимо столбцов, добавленных к выходам вышестоящих и нижестоящих компонентов.  
  
### <a name="processing-rows"></a>Обработка строк  
  
#### <a name="caching-input-rows"></a>Кэширование входных строк  
 При создании компонента с асинхронными выходами есть три способа добавления строк к выходному буферу. Можно добавлять их по мере получения входных строк, кэшировать их, пока компонент не получил все строки от вышестоящего компонента, или добавлять их в какой-то другой момент, подходящий для данного конкретного компонента. Выбор метода зависит от потребностей данного компонента. Например, компонент сортировки не может провести сортировку, пока не получит все строки от вышестоящих компонентов. Поэтому он ждет, пока все строки будут прочитаны, прежде чем добавить их в выходной буфер.  
  
 Строки, полученные во входном буфере, должны сохраняться во внутреннем кэше компонента, пока тот не будет готов их обработать. Получаемые из буфера строки могут кэшироваться в таблице данных, многомерном массиве или иной внутренней структуре.  
  
#### <a name="adding-output-rows"></a>Добавление выходных строк  
 Независимо от того, в какой момент строки добавляются к выходному буферу — по мере получения или после получения всех строк, — добавление производится вызовом метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> выходного буфера. Добавив строку, нужно задать значения всех столбцов новой строки.  
  
 Поскольку в выходном буфере иногда бывает больше столбцов, чем в коллекции выходных столбцов компонента, до присвоения значения очередному столбцу буфера нужно узнать индекс этого столбца. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> возвращает индекс столбца буферной строки с соответствующим идентификатором журнала преобразований. Этот индекс затем используется для присвоения значения столбцу в буфере.  
  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, вызываемый до методов <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>, — первый метод, в котором доступно свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>, и предоставляет первую возможность определить индексы столбцов во входном и выходном буферах.  
  
## <a name="sample"></a>Образец  
 В следующем образце демонстрируется простой компонент преобразования с асинхронными выходами, добавляющий строки к выходному буферу по мере их получения. В этом образце показаны не все методы и возможности, описанные в данном разделе. Он демонстрирует важные методы, с помощью которых должен переопределяться любой создаваемый пользователем компонент преобразования с асинхронными выходами, но не содержит кода для проверки во время разработки. Кроме того, код метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> предполагает, что коллекция выходных столбцов содержит по одному столбцу на каждый столбец коллекции входных столбцов.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
   [DtsPipelineComponent(DisplayName = "AsynchronousOutput")]  
   public class AsynchronousOutput : PipelineComponent  
   {  
      PipelineBuffer outputBuffer;  
      int[] inputColumnBufferIndexes;  
      int[] outputColumnBufferIndexes;  
  
      public override void ProvideComponentProperties()  
      {  
         // Let the base class add the input and output objects.  
         base.ProvideComponentProperties();  
  
         // Name the input and output, and make the  
         // output asynchronous.  
         ComponentMetaData.InputCollection[0].Name = "Input";  
         ComponentMetaData.OutputCollection[0].Name = "AsyncOutput";  
         ComponentMetaData.OutputCollection[0].SynchronousInputID = 0;  
      }  
      public override void PreExecute()  
      {  
         IDTSInput100 input = ComponentMetaData.InputCollection[0];  
         IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
         inputColumnBufferIndexes = new int[input.InputColumnCollection.Count];  
         outputColumnBufferIndexes = new int[output.OutputColumnCollection.Count];  
  
         for (int col = 0; col < input.InputColumnCollection.Count; col++)  
            inputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[col].LineageID);  
  
         for (int col = 0; col < output.OutputColumnCollection.Count; col++)  
            outputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[col].LineageID);  
  
      }  
  
      public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)  
      {  
         if (buffers.Length != 0)  
            outputBuffer = buffers[0];  
      }  
      public override void ProcessInput(int inputID, PipelineBuffer buffer)  
      {  
            // Advance the buffer to the next row.  
            while (buffer.NextRow())  
            {  
               // Add a row to the output buffer.  
               outputBuffer.AddRow();  
               for (int x = 0; x < inputColumnBufferIndexes.Length; x++)  
               {  
                  // Copy the data from the input buffer column to the output buffer column.  
                  outputBuffer[outputColumnBufferIndexes[x]] = buffer[inputColumnBufferIndexes[x]];  
               }  
            }  
         if (buffer.EndOfRowset)  
         {  
            // EndOfRowset on the input buffer is true.  
            // Set EndOfRowset on the output buffer.  
            outputBuffer.SetEndOfRowset();  
         }  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
Namespace Microsoft.Samples.SqlServer.Dts  
  
    <DtsPipelineComponent(DisplayName:="AsynchronousOutput")> _  
    Public Class AsynchronousOutput  
  
        Inherits PipelineComponent  
  
        Private outputBuffer As PipelineBuffer  
        Private inputColumnBufferIndexes As Integer()  
        Private outputColumnBufferIndexes As Integer()  
  
        Public Overrides Sub ProvideComponentProperties()  
  
            ' Let the base class add the input and output objects.  
            Me.ProvideComponentProperties()  
  
            ' Name the input and output, and make the  
            ' output asynchronous.  
            ComponentMetaData.InputCollection(0).Name = "Input"  
            ComponentMetaData.OutputCollection(0).Name = "AsyncOutput"  
            ComponentMetaData.OutputCollection(0).SynchronousInputID = 0  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
            Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
            ReDim inputColumnBufferIndexes(input.InputColumnCollection.Count)  
            ReDim outputColumnBufferIndexes(output.OutputColumnCollection.Count)  
  
            For col As Integer = 0 To input.InputColumnCollection.Count  
                inputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(col).LineageID)  
            Next  
  
            For col As Integer = 0 To output.OutputColumnCollection.Count  
                outputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(col).LineageID)  
            Next  
  
        End Sub  
        Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())  
  
            If buffers.Length <> 0 Then  
                outputBuffer = buffers(0)  
            End If  
  
        End Sub  
  
        Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
                ' Advance the buffer to the next row.  
                While (buffer.NextRow())  
  
                    ' Add a row to the output buffer.  
                    outputBuffer.AddRow()  
                    For x As Integer = 0 To inputColumnBufferIndexes.Length  
  
                        ' Copy the data from the input buffer column to the output buffer column.  
                        outputBuffer(outputColumnBufferIndexes(x)) = buffer(inputColumnBufferIndexes(x))  
  
                    Next  
                End While  
  
            If buffer.EndOfRowset = True Then  
                ' EndOfRowset on the input buffer is true.  
                ' Set the end of row set on the output buffer.  
                outputBuffer.SetEndOfRowset()  
            End If  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>См. также:  
 [Разработка пользовательского компонента преобразования с синхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)   
 [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
