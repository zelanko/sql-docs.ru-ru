---
title: Разработка пользовательского компонента источника | Документы Майкрософт
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
- validation [Integration Services], components
- external data sources [Integration Services]
- data flow components [Integration Services], source components
- output columns [Integration Services]
- custom data flow components [Integration Services], source components
- custom sources [Integration Services]
- source components [Integration Services]
ms.assetid: 4dc0f631-8fd6-4007-b573-ca67f58ca068
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3ea069983515564225d0cf6b74e3660f6ef0829e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768950"
---
# <a name="developing-a-custom-source-component"></a>Разработка пользовательского компонента источника
  Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют разработчикам возможность создавать компоненты источника, которые могут подключаться к пользовательским источникам данных и предоставлять данные из этих источников другим компонентам в задаче потока данных. Возможность создавать пользовательские источники становится полезной, если возникает необходимость подключаться к источникам данных, доступ к которым нельзя получить с помощью одного из существующих источников служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Компоненты источника имеют один или несколько выходов и не имеют входов. Во время разработки компоненты источника используются для создания и настройки соединений, чтения метаданных столбца из внешнего источника данных и настройки выходных столбцов источника, исходя из внешнего источника данных. Во время выполнения они подключаются к внешнему источнику данных и добавляют строки в выходной буфер. Затем задача потока данных предоставляет этот буфер со строками данных для нижестоящих компонентов.  
  
 Общие сведения о разработке компонентов потока данных см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="design-time"></a>Время разработки  
 Реализация функциональных возможностей времени разработки для компонента источника включает указание соединения с внешним источником данных, добавление и настройку выходных столбцов, которые отражают источник данных, а также проверку готовности компонента к выполнению. По определению, компонент источника не имеет входов и один или несколько асинхронных выходов.  
  
### <a name="creating-the-component"></a>Создание компонента  
 Компоненты источника подключаются к внешним источникам данных с помощью объектов <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, определенных в пакете. Они указывают свои требования для диспетчера соединений, добавляя элемент к коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Эта коллекция предназначена для двух целей: хранение ссылок на диспетчеры подключений в пакете, используемом компонентом, и объявление необходимости диспетчера подключений для конструктора. При добавлении объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> к коллекции в окне **Расширенный редактор** отображается вкладка **Свойства соединения**, которая позволяет пользователям выбрать или создать соединение в пакете.  
  
 В следующем примере кода показана реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, который добавляет выход, а также добавляет объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> к коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.OleDb;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "MySourceComponent",ComponentType = ComponentType.SourceAdapter)]  
    public class MyComponent : PipelineComponent  
    {  
        public override void ProvideComponentProperties()  
        {  
            // Reset the component.  
            base.RemoveAllInputsOutputsAndCustomProperties();  
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();  
  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
  
            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();  
            connection.Name = "ADO.NET";  
        }  
```  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="MySourceComponent", ComponentType:=ComponentType.SourceAdapter)> _  
Public Class MySourceComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Allow for resetting the component.  
        RemoveAllInputsOutputsAndCustomProperties()  
        ComponentMetaData.RuntimeConnectionCollection.RemoveAll()  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
  
        Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()  
        connection.Name = "ADO.NET"  
  
    End Sub  
End Class  
```  
  
### <a name="connecting-to-an-external-data-source"></a>Соединение с внешним источником данных  
 После добавления соединения к коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> необходимо переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>, чтобы установить соединение с внешним источником данных. Этот метод вызывается и во время проектирования, и во время выполнения. Компонент должен установить соединение с диспетчером соединений, указанным с помощью соединения времени выполнения, а впоследствии — с внешним источником данных.  
  
 Установленное соединение необходимо кэшировать в компоненте и затем освободить после вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> вызывается и во время проектирования, и во время выполнения, как и метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>. Разработчики переопределяют этот метод и освобождают соединение, установленное компонентом во время вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.  
  
 В следующем примере кода показан компонент, который подключается к соединению ADO.NET в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> и закрывает соединение в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>.  
  
```csharp  
private SqlConnection sqlConnection;  
  
public override void AcquireConnections(object transaction)  
{  
    if (ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager != null)  
    {  
        ConnectionManager cm = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager);  
        ConnectionManagerAdoNet cmado = cm.InnerObject as ConnectionManagerAdoNet;  
  
        if (cmado == null)  
            throw new Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.");  
  
        sqlConnection = cmado.AcquireConnection(transaction) as SqlConnection;  
        sqlConnection.Open();  
    }  
}  
  
public override void ReleaseConnections()  
{  
    if (sqlConnection != null && sqlConnection.State != ConnectionState.Closed)  
        sqlConnection.Close();  
}  
```  
  
```vb  
Private sqlConnection As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal transaction As Object)  
  
    If Not IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) Then  
  
        Dim cm As ConnectionManager = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)  
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject, ConnectionManagerAdoNet)  
  
        If IsNothing(cmado) Then  
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")  
        End If  
  
        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)  
        sqlConnection.Open()  
  
    End If  
End Sub  
  
Public Overrides Sub ReleaseConnections()  
  
    If Not IsNothing(sqlConnection) And sqlConnection.State <> ConnectionState.Closed Then  
        sqlConnection.Close()  
    End If  
  
End Sub  
```  
  
### <a name="creating-and-configuring-output-columns"></a>Создание и настройка выходных столбцов  
 Выходные столбцы компонента источника отражают столбцы из внешнего источника данных, который добавляется компонентом к потоку данных во время выполнения. Во время разработки выходные столбцы добавляются после настройки компонента для подключения к внешнему источнику данных. Метод времени разработки, используемый компонентом для добавления столбцов к своей выходной коллекции, может изменяться в зависимости от потребностей компонента, хотя эти столбцы не должны добавляться во время выполнения методов <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> или <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>. Например, компонент, содержащий инструкцию SQL в пользовательском свойстве, которое управляет набором данных для компонента, может добавлять свои выходные столбцы во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A>. Компонент проверяет, хранится ли в нем кэшированное соединение, и если оно имеется, подключается к источнику данных и создает выходные столбцы.  
  
 После создания выходного столбца компонент задает для него свойства типа данных, вызывая метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A>. Этот метод необходим, поскольку свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> допускают только чтение, причем параметры каждого свойства зависят от параметров другого. Применение данного метода подчеркивает необходимость задавать эти значения единообразно, а задача потока данных проверяет, заданы ли значения правильно.  
  
 Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> столбца определяет значения, задаваемые для других свойств. В следующей таблице показаны требования к зависимым свойствам для каждого значения <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>. Для не указанных здесь типов данных зависимые свойства имеют нулевые значения.  
  
|DataType|Длина|Масштаб|Точность|CodePage|  
|--------------|------------|-----------|---------------|--------------|  
|DT_DECIMAL|0|Больше 0 и меньше или равно 28.|0|0|  
|DT_CY|0|0|0|0|  
|DT_NUMERIC|0|Больше 0, меньше или равно 28 и меньше, чем точность.|Больше или равно 1 и меньше или равно 38.|0|  
|DT_BYTES|Больше 0.|0|0|0|  
|DT_STR|Больше 0 и меньше 8000.|0|0|Не равно 0 и представляет допустимую кодовую страницу.|  
|DT_WSTR|Больше 0 и меньше 4 000.|0|0|0|  
  
 Поскольку ограничения свойств типа данных основаны на типе данных выходного столбца, во время работы с управляемыми типами необходимо выбрать правильный тип данных служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. В базовом классе предусмотрены три вспомогательных метода: <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>, позволяющие разработчикам управляемых компонентов выбрать тип данных служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] с учетом управляемого типа. Эти методы преобразуют управляемые типы данных в типы данных служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] и обратно.  
  
 В следующем примере кода показано, как происходит заполнение коллекции выходных столбцов компонента на основе схемы таблицы. Вспомогательные методы базового класса используются для задания типа данных столбца, а зависимые свойства задаются с учетом типа данных.  
  
```csharp  
SqlCommand sqlCommand;  
  
private void CreateColumnsFromDataTable()  
{  
    // Get the output.  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    // Start clean, and remove the columns from both collections.  
    output.OutputColumnCollection.RemoveAll();  
    output.ExternalMetadataColumnCollection.RemoveAll();  
  
    this.sqlCommand = sqlConnection.CreateCommand();  
    this.sqlCommand.CommandType = CommandType.Text;  
    this.sqlCommand.CommandText = (string)ComponentMetaData.CustomPropertyCollection["SqlStatement"].Value;  
    SqlDataReader schemaReader = this.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly);  
    DataTable dataTable = schemaReader.GetSchemaTable();  
  
    // Walk the columns in the schema,   
    // and for each data column create an output column and an external metadata column.  
    foreach (DataRow row in dataTable.Rows)  
    {  
        IDTSOutputColumn100 outColumn = output.OutputColumnCollection.New();  
        IDTSExternalMetadataColumn100 exColumn = output.ExternalMetadataColumnCollection.New();  
  
        // Set column data type properties.  
        bool isLong = false;  
        DataType dt = DataRecordTypeToBufferType((Type)row["DataType"]);  
        dt = ConvertBufferDataTypeToFitManaged(dt, ref isLong);  
        int length = 0;  
        int precision = (short)row["NumericPrecision"];  
        int scale = (short)row["NumericScale"];  
        int codepage = dataTable.Locale.TextInfo.ANSICodePage;  
  
        switch (dt)  
        {  
            // The length cannot be zero, and the code page property must contain a valid code page.  
            case DataType.DT_STR:  
            case DataType.DT_TEXT:  
                length = precision;  
                precision = 0;  
                scale = 0;  
                break;  
  
            case DataType.DT_WSTR:  
                length = precision;  
                codepage = 0;  
                scale = 0;  
                precision = 0;  
                break;  
  
            case DataType.DT_BYTES:  
                precision = 0;  
                scale = 0;  
                codepage = 0;  
                break;  
  
            case DataType.DT_NUMERIC:  
                length = 0;  
                codepage = 0;  
  
                if (precision > 38)  
                    precision = 38;  
  
                if (scale > 6)  
                    scale = 6;  
                break;  
  
            case DataType.DT_DECIMAL:  
                length = 0;  
                precision = 0;  
                codepage = 0;  
                break;  
  
            default:  
                length = 0;  
                precision = 0;  
                codepage = 0;  
                scale = 0;  
                break;  
  
        }  
  
        // Set the properties of the output column.  
        outColumn.Name = (string)row["ColumnName"];  
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage);  
    }  
}  
```  
  
```vb  
Private sqlCommand As SqlCommand  
  
Private Sub CreateColumnsFromDataTable()  
  
    ' Get the output.  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ' Start clean, and remove the columns from both collections.  
    output.OutputColumnCollection.RemoveAll()  
    output.ExternalMetadataColumnCollection.RemoveAll()  
  
    Me.sqlCommand = sqlConnection.CreateCommand()  
    Me.sqlCommand.CommandType = CommandType.Text  
    Me.sqlCommand.CommandText = CStr(ComponentMetaData.CustomPropertyCollection("SqlStatement").Value)  
  
    Dim schemaReader As SqlDataReader = Me.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly)  
    Dim dataTable As DataTable = schemaReader.GetSchemaTable()  
  
    ' Walk the columns in the schema,   
    ' and for each data column create an output column and an external metadata column.  
    For Each row As DataRow In dataTable.Rows  
  
        Dim outColumn As IDTSOutputColumn100 = output.OutputColumnCollection.New()  
        Dim exColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()  
  
        ' Set column data type properties.  
        Dim isLong As Boolean = False  
        Dim dt As DataType = DataRecordTypeToBufferType(CType(row("DataType"), Type))  
        dt = ConvertBufferDataTypeToFitManaged(dt, isLong)  
        Dim length As Integer = 0  
        Dim precision As Integer = CType(row("NumericPrecision"), Short)  
        Dim scale As Integer = CType(row("NumericScale"), Short)  
        Dim codepage As Integer = dataTable.Locale.TextInfo.ANSICodePage  
  
        Select Case dt  
  
            ' The length cannot be zero, and the code page property must contain a valid code page.  
            Case DataType.DT_STR  
            Case DataType.DT_TEXT  
                length = precision  
                precision = 0  
                scale = 0  
  
            Case DataType.DT_WSTR  
                length = precision  
                codepage = 0  
                scale = 0  
                precision = 0  
  
            Case DataType.DT_BYTES  
                precision = 0  
                scale = 0  
                codepage = 0  
  
            Case DataType.DT_NUMERIC  
                length = 0  
                codepage = 0  
  
                If precision > 38 Then  
                    precision = 38  
                End If  
  
                If scale > 6 Then  
                    scale = 6  
                End If  
  
            Case DataType.DT_DECIMAL  
                length = 0  
                precision = 0  
                codepage = 0  
  
            Case Else  
                length = 0  
                precision = 0  
                codepage = 0  
                scale = 0  
        End Select  
  
        ' Set the properties of the output column.  
        outColumn.Name = CStr(row("ColumnName"))  
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage)  
    Next  
End Sub  
```  
  
### <a name="validating-the-component"></a>Проверка компонента  
 Необходимо проверить компонент источника и убедиться, что столбцы, определенные в его коллекциях выходных столбцов, совпадают со столбцами во внешнем источнике данных. Иногда сверка выходных столбцов с внешним источником данных может оказаться невозможной, например, если имеет место отсоединенное состояние или желательно обойтись без применения продолжительных операций обмена данными с сервером. В этих ситуациях все равно может быть выполнена проверка столбцов в выходе с помощью коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> выходного объекта. Дополнительные сведения см. в разделе [Проверка компонента потока данных](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).  
  
 Эта коллекция существует и во входных, и в выходных объектах, и ее можно заполнить столбцами из внешнего источника данных. Эту коллекцию можно использовать для проверки выходных столбцов, если конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] находится в режиме вне сети, компонент отсоединен или свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> имеет значение `false`. Эту коллекцию необходимо вначале заполнить одновременно с созданием выходных столбцов. Добавление столбцов внешних метаданных к коллекции происходит относительно просто, поскольку столбец внешних метаданных должен с самого начала совпадать с выходным столбцом. Свойства типа данных столбца уже должны быть заданы правильно, поэтому эти свойства можно скопировать непосредственно в объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>.  
  
 В следующем образце кода добавляется столбец внешних метаданных, который основан на вновь созданном выходном столбце. При этом подразумевается, что выходной столбец уже был создан.  
  
```csharp  
private void CreateExternalMetaDataColumn(IDTSOutput100 output, IDTSOutputColumn100 outputColumn)  
{  
  
    // Set the properties of the external metadata column.  
    IDTSExternalMetadataColumn100 externalColumn = output.ExternalMetadataColumnCollection.New();  
    externalColumn.Name = outputColumn.Name;  
    externalColumn.Precision = outputColumn.Precision;  
    externalColumn.Length = outputColumn.Length;  
    externalColumn.DataType = outputColumn.DataType;  
    externalColumn.Scale = outputColumn.Scale;  
  
    // Map the external column to the output column.  
    outputColumn.ExternalMetadataColumnID = externalColumn.ID;  
  
}  
```  
  
```vb  
Private Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumn As IDTSOutputColumn100)  
  
        ' Set the properties of the external metadata column.  
        Dim externalColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()  
        externalColumn.Name = outputColumn.Name  
        externalColumn.Precision = outputColumn.Precision  
        externalColumn.Length = outputColumn.Length  
        externalColumn.DataType = outputColumn.DataType  
        externalColumn.Scale = outputColumn.Scale  
  
        ' Map the external column to the output column.  
        outputColumn.ExternalMetadataColumnID = externalColumn.ID  
  
    End Sub  
```  
  
## <a name="run-time"></a>Время выполнения  
 Во время выполнения компоненты добавляют строки в выходные буферы, созданные задачей потока данных и предоставленные компоненту в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>. Этот метод, вызываемый однократно для компонентов источника, получает выходной буфер для каждого объекта <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> компонента, который подключен к нижестоящему компоненту.  
  
### <a name="locating-columns-in-the-buffer"></a>Поиск столбцов в буфере  
 Выходной буфер для компонента содержит столбцы, определенные компонентом, и все столбцы, добавленные к выходу нижестоящего компонента. Например, если компонент источника предоставляет три столбца на выходе, а в следующем компоненте добавляется четвертый выходной столбец, то выходной буфер, предназначенный для использования компонентом источника, содержит эти четыре столбца.  
  
 Порядок столбцов в строке буфера не определяется индексом выходного столбца в коллекции выходных столбцов. Выходной столбец можно точно найти в строке буфера только с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> объекта <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>. Этот метод находит столбец с указанным идентификатором журнала обращений и преобразований в указанном буфере, после чего возвращает его расположение в строке. Индексы выходных столбцов обычно определяются в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> и сохраняются для использования во время выполнения метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.  
  
 В следующем примере кода находится расположение выходных столбцов в выходном буфере во время вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> и полученные данные сохраняются во внутренней структуре. В структуре сохраняется также имя столбца, которое затем используется в примере кода, относящемся к методу <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, в следующем подразделе этого раздела.  
  
```csharp  
ArrayList columnInformation;  
  
private struct ColumnInfo  
{  
    public int BufferColumnIndex;  
    public string ColumnName;  
}  
  
public override void PreExecute()  
{  
    this.columnInformation = new ArrayList();  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    foreach (IDTSOutputColumn100 col in output.OutputColumnCollection)  
    {  
        ColumnInfo ci = new ColumnInfo();  
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID);  
        ci.ColumnName = col.Name;  
        columnInformation.Add(ci);  
    }  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Me.columnInformation = New ArrayList()  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    For Each col As IDTSOutputColumn100 In output.OutputColumnCollection  
  
        Dim ci As ColumnInfo = New ColumnInfo()  
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID)  
        ci.ColumnName = col.Name  
        columnInformation.Add(ci)  
    Next  
End Sub  
```  
  
### <a name="processing-rows"></a>Обработка строк  
 Строки добавляются к выходному буферу путем вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A>, который создает новую строку буфера с пустыми значениями в ее столбцах. Затем компонент присваивает значения отдельным столбцам. Выходные буферы, предоставленные компоненту, создаются и наблюдаются задачей потока данных. По мере их заполнения строки буферы перемещаются в следующий компонент. Невозможно определить время отправки пакета строк в следующий компонент, поскольку перемещение строк задачей потока данных прозрачно для разработчика компонента, а свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> для выходных буферов всегда равно нулю. Компонент источника после завершения добавления строк в выходной буфер уведомляет задачу потока данных путем вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> буфера <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, а оставшиеся в буфере строки передаются следующему компоненту.  
  
 При считывании строк компонентом источника из внешнего источника данных может потребоваться обновить счетчики производительности «Rows read» (Количество считанных строк) или «BLOB bytes read» (Количество считанных байтов больших двоичных объектов) путем вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A>. Дополнительные сведения см. в статье [Performance Counters](../performance/performance-counters.md).  
  
 В следующем примере кода показан компонент, который добавляет строки в выходной буфер в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>. Индексы выходных столбцов в буфере были найдены с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> в предыдущем примере кода.  
  
```csharp  
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)  
{  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
    PipelineBuffer buffer = buffers[0];  
  
    SqlDataReader dataReader = sqlCommand.ExecuteReader();  
  
    // Loop over the rows in the DataReader,   
    // and add them to the output buffer.  
    while (dataReader.Read())  
    {  
        // Add a row to the output buffer.  
        buffer.AddRow();  
  
        for (int x = 0; x < columnInformation.Count; x++)  
        {  
            ColumnInfo ci = (ColumnInfo)columnInformation[x];  
            int ordinal = dataReader.GetOrdinal(ci.ColumnName);  
  
            if (dataReader.IsDBNull(ordinal))  
                buffer.SetNull(ci.BufferColumnIndex);  
            else  
            {  
                buffer[ci.BufferColumnIndex] = dataReader[ci.ColumnName];  
            }  
        }  
    }  
    buffer.SetEndOfRowset();  
}  
```  
  
```vb  
Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())  
  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
    Dim buffer As PipelineBuffer = buffers(0)  
  
    Dim dataReader As SqlDataReader = sqlCommand.ExecuteReader()  
  
    ' Loop over the rows in the DataReader,   
    ' and add them to the output buffer.  
    While (dataReader.Read())  
  
        ' Add a row to the output buffer.  
        buffer.AddRow()  
  
        For x As Integer = 0 To columnInformation.Count  
  
            Dim ci As ColumnInfo = CType(columnInformation(x), ColumnInfo)  
  
            Dim ordinal As Integer = dataReader.GetOrdinal(ci.ColumnName)  
  
            If (dataReader.IsDBNull(ordinal)) Then  
                buffer.SetNull(ci.BufferColumnIndex)  
            Else  
                buffer(ci.BufferColumnIndex) = dataReader(ci.ColumnName)  
  
            End If  
        Next  
  
    End While  
  
    buffer.SetEndOfRowset()  
End Sub  
```  
  
## <a name="sample"></a>Образец  
 В следующем образце показан простой компонент источника, в котором используется диспетчер соединения файлов для загрузки двоичного содержимого из файлов в поток данных. В этом образце показаны не все методы и возможности, описанные в данном разделе. Он демонстрирует важные методы, которые должны быть переопределены в каждом пользовательском компоненте источника, но не содержат код для проверки во время разработки.  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace BlobSrc  
{  
  [DtsPipelineComponent(DisplayName = "BLOB Inserter Source", Description = "Inserts files into the data flow as BLOBs")]  
  public class BlobSrc : PipelineComponent  
  {  
    IDTSConnectionManager100 m_ConnMgr;  
    int m_FileNameColumnIndex = -1;  
    int m_FileBlobColumnIndex = -1;  
  
    public override void ProvideComponentProperties()  
    {  
      IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
      output.Name = "BLOB File Inserter Output";  
  
      IDTSOutputColumn100 column = output.OutputColumnCollection.New();  
      column.Name = "FileName";  
      column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0);  
  
      column = output.OutputColumnCollection.New();  
      column.Name = "FileBLOB";  
      column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0);  
  
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();  
      conn.Name = "FileConnection";  
    }  
  
    public override void AcquireConnections(object transaction)  
    {  
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];  
      m_ConnMgr = conn.ConnectionManager;  
    }  
  
    public override void ReleaseConnections()  
    {  
      m_ConnMgr = null;  
    }  
  
    public override void PreExecute()  
    {  
      IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
      m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[0].LineageID);  
      m_FileBlobColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[1].LineageID);  
    }  
  
    public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)  
    {  
      string strFileName = (string)m_ConnMgr.AcquireConnection(null);  
  
      while (strFileName != null)  
      {  
        buffers[0].AddRow();  
  
        buffers[0].SetString(m_FileNameColumnIndex, strFileName);  
  
        FileInfo fileInfo = new FileInfo(strFileName);  
        byte[] fileData = new byte[fileInfo.Length];  
        FileStream fs = new FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read);  
        fs.Read(fileData, 0, fileData.Length);  
  
        buffers[0].AddBlobData(m_FileBlobColumnIndex, fileData);  
  
        strFileName = (string)m_ConnMgr.AcquireConnection(null);  
      }  
  
      buffers[0].SetEndOfRowset();  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.IO   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace BlobSrc   
  
 <DtsPipelineComponent(DisplayName="BLOB Inserter Source", Description="Inserts files into the data flow as BLOBs")> _   
 Public Class BlobSrc   
 Inherits PipelineComponent   
   Private m_ConnMgr As IDTSConnectionManager100   
   Private m_FileNameColumnIndex As Integer = -1   
   Private m_FileBlobColumnIndex As Integer = -1   
  
   Public  Overrides Sub ProvideComponentProperties()   
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
     output.Name = "BLOB File Inserter Output"   
     Dim column As IDTSOutputColumn100 = output.OutputColumnCollection.New   
     column.Name = "FileName"   
     column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0)   
     column = output.OutputColumnCollection.New   
     column.Name = "FileBLOB"   
     column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0)   
     Dim conn As IDTSRuntimeConnection90 = ComponentMetaData.RuntimeConnectionCollection.New   
     conn.Name = "FileConnection"   
   End Sub   
  
   Public  Overrides Sub AcquireConnections(ByVal transaction As Object)   
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0)   
     m_ConnMgr = conn.ConnectionManager   
   End Sub   
  
   Public  Overrides Sub ReleaseConnections()   
     m_ConnMgr = Nothing   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)   
     m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(0).LineageID), Integer)   
     m_FileBlobColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(1).LineageID), Integer)   
   End Sub   
  
   Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())   
     Dim strFileName As String = CType(m_ConnMgr.AcquireConnection(Nothing), String)   
     While Not (strFileName Is Nothing)   
       buffers(0).AddRow   
       buffers(0).SetString(m_FileNameColumnIndex, strFileName)   
       Dim fileInfo As FileInfo = New FileInfo(strFileName)   
       Dim fileData(fileInfo.Length) As Byte   
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read)   
       fs.Read(fileData, 0, fileData.Length)   
       buffers(0).AddBlobData(m_FileBlobColumnIndex, fileData)   
       strFileName = CType(m_ConnMgr.AcquireConnection(Nothing), String)   
     End While   
     buffers(0).SetEndOfRowset   
   End Sub   
 End Class   
End Namespace  
```  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Разработка пользовательского компонента назначения](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)   
 [Создание источника с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
  
  
