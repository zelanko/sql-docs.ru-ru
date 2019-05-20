---
title: Разработка пользовательского компонента преобразования с синхронными выходами | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
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
- ProcessInput method
- buffer allocations [Integration Services]
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- data flow components [Integration Services], transformation components
ms.assetid: b694d21f-9919-402d-9192-666c6449b0b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5335e93d133787f1ee2f855d3a2eb9ad1faa2824
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65724792"
---
# <a name="developing-a-custom-transformation-component-with-synchronous-outputs"></a>Разработка пользовательского компонента преобразования с синхронными выходами

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Компоненты преобразования с синхронными выходами получают строки из вышестоящих компонентов и считывают либо изменяют значения в столбцах этих строк по мере передачи строк нижестоящим компонентам. В них также можно определить дополнительные выходные столбцы, производные от столбцов, которые передаются вышестоящими компонентами, однако эти столбцы не добавляют строки в поток данных. Дополнительные сведения о различиях между синхронными и асинхронными компонентами см. в разделе [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Компоненты такого типа подходят для задач, в которых данные изменяются встроенными средствами при передаче компоненту, а компоненту необязательно просматривать все строки, прежде чем приступать к их обработке. Это наиболее простой для разработки вид компонента, поскольку преобразования с синхронными выходами обычно не соединяются с внешними источниками данных, не управляют столбцами внешних метаданных и не добавляют строки в выходные буферы.  
  
 Создание компонента преобразования с синхронными выходами предполагает добавление объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>, который содержит вышестоящие столбцы, выбранные для компонента, и объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>, который может содержать производные столбцы, созданные компонентом. Необходимо также реализовать методы времени разработки и предоставить код, осуществляющий считывание или изменение столбцов во входящих строках буфера в процессе выполнения.  
  
 В этом разделе содержатся сведения о том, что требуется для реализации пользовательского компонента преобразования, а также приведены примеры кода, которые помогут лучше понять основные понятия.  
  
## <a name="design-time"></a>Время разработки  
 Код времени разработки для этого компонента включает создание входов и выходов, добавление дополнительных выходных столбцов, формируемых компонентом, и проверку конфигурации компонента.  
  
### <a name="creating-the-component"></a>Создание компонента  
 Создание входов, выходов и пользовательских свойств компонента обычно осуществляется при выполнении метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>. Существует два способа добавления входа и выхода в компонент преобразования с синхронными выходами. Можно использовать реализацию базового класса метода и затем изменить созданные им вход и выход по умолчанию, либо можно явным образом самостоятельно добавить вход и выход.  
  
 В следующем примере кода демонстрируется реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, явно добавляющего объекты входа и выхода. Вызов базового класса, с помощью которого можно достичь того же результата, заключен в комментарий.  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SynchronousComponent", ComponentType = ComponentType.Transform)]  
    public class SyncComponent : PipelineComponent  
    {  
  
        public override void ProvideComponentProperties()  
        {  
            // Add the input.  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            // Add the output.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
            output.SynchronousInputID = input.ID;  
  
            // Alternatively, you can let the base class add the input and output  
            // and set the SynchronousInputID of the output to the ID of the input.  
            // base.ProvideComponentProperties();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="SynchronousComponent", ComponentType:=ComponentType.Transform)> _  
Public Class SyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Add the input.  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
        input.Name = "Input"  
  
        ' Add the output.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
        output.SynchronousInputID = Input.ID  
  
        ' Alternatively, you can let the base class add the input and output  
        ' and set the SynchronousInputID of the output to the ID of the input.  
        ' base.ProvideComponentProperties();  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a>Создание и настройка выходных столбцов  
 Хотя компоненты преобразования с синхронными выходами не добавляют строки в буферы, они могут добавлять дополнительные выходные столбцы в собственный выход. Как правило, при добавлении компонентом выходного столбца значения нового выходного столбца производятся во время выполнения от данных, содержащихся в одном или нескольких столбцах, переданных компоненту вышестоящим компонентом.  
  
 После создания выходного столбца необходимо задать для него свойства типа данных. Задание свойств типа данных выходного столбца требует специальной обработки и осуществляется путем вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A>. Использование этого метода необходимо, поскольку свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> по отдельности доступны только для чтения по причине зависимости каждого из них от настроек других. Этот метод гарантирует согласованность задания значений свойств, а задача потока данных осуществляет проверку правильности задания значений.  
  
 Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> столбца определяет значения, задаваемые для других свойств. В следующей таблице показаны требования к зависимым свойствам для каждого значения <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>. Для не указанных здесь типов данных зависимые свойства имеют нулевые значения.  
  
|DataType|Длина|Масштаб|Точность|CodePage|  
|--------------|------------|-----------|---------------|--------------|  
|DT_DECIMAL|0|Больше 0 и меньше или равно 28.|0|0|  
|DT_CY|0|0|0|0|  
|DT_NUMERIC|0|Больше 0, меньше или равно 28 и меньше, чем точность.|Больше или равно 1 и меньше или равно 38.|0|  
|DT_BYTES|Больше 0.|0|0|0|  
|DT_STR|Больше 0 и меньше 8000.|0|0|Не равно 0 и представляет допустимую кодовую страницу.|  
|DT_WSTR|Больше 0 и меньше 4 000.|0|0|0|  
  
 Поскольку ограничения свойств типа данных основаны на типе данных выходного столбца, во время работы с управляемыми типами необходимо выбрать правильный тип данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Базовый класс предоставляет три вспомогательных метода, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>, которые упрощают для разработчиков управляемых компонентов выбор типа данных служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], если необходим управляемый тип. Эти методы преобразуют управляемые типы данных в типы данных служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] и обратно.  
  
## <a name="run-time"></a>Время выполнения  
 Обычно реализация части компонента, которая относится ко времени выполнения, заключается в решении двух задач — поиска входных и выходных столбцов компонента в буфере и считывания либо записи значений этих столбцов во входящие строки буфера.  
  
### <a name="locating-columns-in-the-buffer"></a>Поиск столбцов в буфере  
 Количество столбцов в буферах, передаваемых компоненту во время выполнения, скорее всего, окажется больше числа столбцов во входных и выходных коллекциях компонента. Так происходит потому, что каждый буфер содержит все выходные столбцы, определенные в компонентах потока данных. Чтобы обеспечить правильное сопоставление столбцов буфера со столбцами входа и выхода, разработчикам компонентов следует использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> диспетчера буферов <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>. Этот метод осуществляет поиск столбца в указанном буфере по его идентификатору журнала преобразований. Обычно поиск столбцов производится в процессе выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, поскольку это первый метод времени выполнения, в котором становится доступным свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.  
  
 В следующем примере кода демонстрируется компонент, осуществляющий поиск индексов столбцов в своей коллекции входных и выходных столбцов в процессе выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>. Индексы столбцов хранятся в целочисленном массиве, и доступ к ним компонент может получить в процессе выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
```csharp  
int []inputColumns;  
int []outputColumns;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    inputColumns = new int[input.InputColumnCollection.Count];  
    outputColumns = new int[output.OutputColumnCollection.Count];  
  
    for(int col=0; col < input.InputColumnCollection.Count; col++)  
    {  
        IDTSInputColumn100 inputColumn = input.InputColumnCollection[col];  
        inputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID);  
    }  
  
    for(int col=0; col < output.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 outputColumn = output.OutputColumnCollection[col];  
        outputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID);  
    }  
  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ReDim inputColumns(input.InputColumnCollection.Count)  
    ReDim outputColumns(output.OutputColumnCollection.Count)  
  
    For col As Integer = 0 To input.InputColumnCollection.Count  
  
        Dim inputColumn As IDTSInputColumn100 = input.InputColumnCollection(col)  
        inputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID)  
    Next  
  
    For col As Integer = 0 To output.OutputColumnCollection.Count  
  
        Dim outputColumn As IDTSOutputColumn100 = output.OutputColumnCollection(col)  
        outputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID)  
    Next  
  
End Sub  
```  
  
### <a name="processing-rows"></a>Обработка строк  
 Компоненты получают объекты <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, содержащие строки и столбцы, в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. При выполнении этого метода осуществляется итерация по строкам в буфере, а столбцы, идентифицированные во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, считываются и изменяются. Метод вызывается задачей потока данных повторно до тех пор, пока не останется строк, переданных из вышестоящего компонента.  
  
 Считывание или запись отдельного столбца в буфере осуществляется с использованием индексатора массива в качестве метода доступа либо с помощью одного из методов **Get** или **Set**. Методы **Get** и **Set** более эффективны. Их следует использовать в случаях, когда тип данных столбца в буфере известен.  
  
 В следующем примере кода демонстрируется реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>, обрабатывающего входящие строки.  
  
```csharp  
public override void ProcessInput( int InputID, PipelineBuffer buffer)  
{  
       while( buffer.NextRow())  
       {  
            for(int x=0; x < inputColumns.Length;x++)  
            {  
                if(!buffer.IsNull(inputColumns[x]))  
                {  
                    object columnData = buffer[inputColumns[x]];  
                    // TODO: Modify the column data.  
                    buffer[inputColumns[x]] = columnData;  
                }  
            }  
  
      }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal InputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For x As Integer = 0 To inputColumns.Length  
  
                if buffer.IsNull(inputColumns(x)) = false then  
  
                    Dim columnData As Object = buffer(inputColumns(x))  
                    ' TODO: Modify the column data.  
                    buffer(inputColumns(x)) = columnData  
  
                End If  
            Next  
  
        End While  
End Sub  
```  
  
## <a name="sample"></a>Образец  
 В следующем образце демонстрируется простой компонент преобразования с синхронными выходами, изменяющий регистр значений всех символьных столбцов на верхний. В этом образце показаны не все методы и возможности, описанные в данном разделе. В этом образце демонстрируются важные методы, которые должны быть переопределены каждым пользовательским компонентом преобразования с синхронными выходами, но отсутствует код для проверки во время разработки.  
  
```csharp  
using System;  
using System.Collections;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Uppercase  
{  
  [DtsPipelineComponent(DisplayName = "Uppercase")]  
  public class Uppercase : PipelineComponent  
  {  
    ArrayList m_ColumnIndexList = new ArrayList();  
  
    public override void ProvideComponentProperties()  
    {  
      base.ProvideComponentProperties();  
      ComponentMetaData.InputCollection[0].Name = "Uppercase Input";  
      ComponentMetaData.OutputCollection[0].Name = "Uppercase Output";  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        if (column.DataType == DataType.DT_STR || column.DataType == DataType.DT_WSTR)  
        {  
          m_ColumnIndexList.Add((int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID));  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        foreach (int columnIndex in m_ColumnIndexList)  
        {  
          string str = buffer.GetString(columnIndex);  
          buffer.SetString(columnIndex, str.ToUpper());  
        }  
      }  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.Collections   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace Uppercase   
  
 <DtsPipelineComponent(DisplayName="Uppercase")> _   
 Public Class Uppercase   
 Inherits PipelineComponent   
   Private m_ColumnIndexList As ArrayList = New ArrayList   
  
   Public  Overrides Sub ProvideComponentProperties()   
     MyBase.ProvideComponentProperties   
     ComponentMetaData.InputCollection(0).Name = "Uppercase Input"   
     ComponentMetaData.OutputCollection(0).Name = "Uppercase Output"   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     For Each column As IDTSInputColumn100 In inputColumns   
       If column.DataType = DataType.DT_STR OrElse column.DataType = DataType.DT_WSTR Then   
         m_ColumnIndexList.Add(CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer))   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       For Each columnIndex As Integer In m_ColumnIndexList   
         Dim str As String = buffer.GetString(columnIndex)   
         buffer.SetString(columnIndex, str.ToUpper)   
       Next   
     End While   
   End Sub   
 End Class   
End Namespace  
```  
  
## <a name="see-also"></a>См. также:  
 [Разработка пользовательского компонента преобразования с асинхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)   
 [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
  
  
