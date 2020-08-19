---
description: Разработка пользовательского компонента назначения
title: Разработка пользовательского компонента назначения | Документы Майкрософт
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
- validation [Integration Services], components
- destinations [Integration Services], components
- ProcessInput method
- external data sources [Integration Services]
- custom data flow components [Integration Services], destination components
- data flow components [Integration Services], destination components
ms.assetid: 24619363-9535-4c0e-8b62-1d22c6630e40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f681c33f7921f57d42f9078a768f8f8eafec1f7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88391250"
---
# <a name="developing-a-custom-destination-component"></a>Разработка пользовательского компонента назначения

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют разработчикам возможность создания пользовательских компонентов назначения, которые могут соединяться с любым пользовательским источником данных и хранить в нем свои данные. Пользовательские компоненты назначения полезны при необходимости соединения с источниками данных, доступ к которым не может быть осуществлен с помощью одного из существующих исходных компонентов, включенных в службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Компоненты назначения имеют один или несколько входов и ни одного выхода. Во время разработки они создают и настраивают соединения и считывают метаданные столбцов из внешнего источника данных. Во время выполнения они соединяются с внешним источником данных и добавляют строки, получаемые от вышестоящих компонентов в потоке данных внешнего источника данных. Если внешний источник данных уже существует к моменту выполнения компонента, компонент назначения должен также убедиться, что типы данных столбцов, получаемых компонентом, соответствуют типам данных столбцов внешнего источника данных.  
  
 В этом разделе подробно описана разработка компонентов назначения и приведены примеры кода, поясняющие важные основные понятия. Общие сведения о разработке компонентов потока данных см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="design-time"></a>Время разработки  
 Реализация для компонента назначения функциональности времени разработки включает указание соединения с внешним источником данных и проверку правильности настройки компонента. Компонент назначения по определению имеет один вход и, возможно, один выход для вывода ошибок.  
  
### <a name="creating-the-component"></a>Создание компонента  
 Компоненты назначения соединяются с внешними источниками данных при помощи определенных в пакете объектов <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>. Компонент назначения указывает конструктору служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] и пользователям компонента, что ему необходим диспетчер подключений, добавляя элемент в коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> объекта <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Коллекция служит двум целям. Во-первых, она извещает конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] о потребности в диспетчере подключений. Во-вторых, после выбора или создания пользователем диспетчера подключений она хранит ссылку на него в пакете, используемом компонентом. Когда объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> добавляется в коллекцию, в **расширенном редакторе** открывается вкладка **Свойства соединения**, предлагающая пользователю выбрать или создать в пакете соединение, которое будет использоваться компонентом.  
  
 Следующий образец кода иллюстрирует реализацию метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, который добавляет вход и объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> в коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "Destination Component",ComponentType =ComponentType.DestinationAdapter)]  
    public class DestinationComponent : PipelineComponent   
    {  
        public override void ProvideComponentProperties()  
        {  
            // Reset the component.  
            base.RemoveAllInputsOutputsAndCustomProperties();  
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();  
  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();  
            connection.Name = "ADO.net";  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Namespace Microsoft.Samples.SqlServer.Dts  
  
    <DtsPipelineComponent(DisplayName:="Destination Component", ComponentType:=ComponentType.DestinationAdapter)> _  
    Public Class DestinationComponent  
        Inherits PipelineComponent  
  
        Public Overrides Sub ProvideComponentProperties()  
  
            ' Reset the component.  
            Me.RemoveAllInputsOutputsAndCustomProperties()  
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll()  
  
            Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
            input.Name = "Input"  
  
            Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()  
            connection.Name = "ADO.net"  
  
        End Sub  
    End Class  
End Namespace  
```  
  
### <a name="connecting-to-an-external-data-source"></a>Соединение с внешним источником данных  
 После добавления соединения в коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> необходимо переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> для установления соединения с внешним источником данных. Этот метод вызывается во время разработки и во время выполнения. Компонент должен установить соединение с диспетчером соединений, определенным соединением времени выполнения, а затем соединение с внешним источником данных. После того как соединение установлено, компонент должен сохранить его во внутреннем кэше и освободить при вызове метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>. Разработчики переопределяют этот метод и освобождают соединение, установленное компонентом во время вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>. Оба метода, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>, вызываются как во время разработки, так и во время выполнения.  
  
 Следующий пример кода иллюстрирует соединение компонента с ADO.NET в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> и закрытие соединения в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>.  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
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
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
Private sqlConnection As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal transaction As Object)  
  
    If IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) = False Then  
  
        Dim cm As ConnectionManager = DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)  
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject,ConnectionManagerAdoNet)  
  
        If IsNothing(cmado) Then  
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")  
        End If  
  
        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)  
        sqlConnection.Open()  
  
    End If  
End Sub  
  
Public Overrides Sub ReleaseConnections()  
  
    If IsNothing(sqlConnection) = False And sqlConnection.State <> ConnectionState.Closed Then  
        sqlConnection.Close()  
    End If  
  
End Sub  
```  
  
### <a name="validating-the-component"></a>Проверка компонента  
 Разработчики компонентов назначения должны производить проверку, описанную в разделе [Проверка компонентов](../../integration-services/extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md). Кроме того, они должны проверять, что свойства типа данных столбцов, определенных в коллекции входных столбцов компонентов, соответствуют столбцам внешнего источника данных. Иногда проверка входных столбцов на соответствие с внешним источником данных невозможна или нежелательна — например, если компонент или конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] отсоединены либо пересылка данных на сервер и обратно неприемлема. Однако и в этой ситуации можно выполнить проверку столбцов в коллекции входных столбцов с помощью коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ExternalMetadataColumnCollection%2A> входного объекта.  
  
 Эта коллекция имеется как у входных, так и выходных объектов и должна быть заполнена разработчиком компонента данными о столбцах внешнего источника данных. Эту коллекцию можно использовать для проверки входных столбцов, если конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] нет в сети, если компонент не подключен либо если свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> имеет значение **false**.  
  
 Следующий образец кода добавляет столбец внешних метаданных, основываясь на данных о существующем входном столбце.  
  
```csharp  
private void AddExternalMetaDataColumn(IDTSInput100 input,IDTSInputColumn100 inputColumn)  
{  
    // Set the properties of the external metadata column.  
    IDTSExternalMetadataColumn100 externalColumn = input.ExternalMetadataColumnCollection.New();  
    externalColumn.Name = inputColumn.Name;  
    externalColumn.Precision = inputColumn.Precision;  
    externalColumn.Length = inputColumn.Length;  
    externalColumn.DataType = inputColumn.DataType;  
    externalColumn.Scale = inputColumn.Scale;  
  
    // Map the external column to the input column.  
    inputColumn.ExternalMetadataColumnID = externalColumn.ID;  
}  
```  
  
```vb  
Private Sub AddExternalMetaDataColumn(ByVal input As IDTSInput100, ByVal inputColumn As IDTSInputColumn100)  
  
    ' Set the properties of the external metadata column.  
    Dim externalColumn As IDTSExternalMetadataColumn100 = input.ExternalMetadataColumnCollection.New()  
    externalColumn.Name = inputColumn.Name  
    externalColumn.Precision = inputColumn.Precision  
    externalColumn.Length = inputColumn.Length  
    externalColumn.DataType = inputColumn.DataType  
    externalColumn.Scale = inputColumn.Scale  
  
    ' Map the external column to the input column.  
    inputColumn.ExternalMetadataColumnID = externalColumn.ID  
  
End Sub  
```  
  
## <a name="run-time"></a>Время выполнения  
 Во время выполнения компонент назначения получает вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> каждый раз, когда заполняется буфер <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> данными из вышестоящего компонента. Метод вызывается повторно до тех пор, пока не закончатся буферы и пока свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> не примет значение **true**. Во время выполнения этого метода компоненты назначения считывают из буфера столбцы и строки и добавляют их во внешний источник данных.  
  
### <a name="locating-columns-in-the-buffer"></a>Поиск столбцов в буфере  
 Входной буфер для компонента содержит все столбцы, определенные в коллекциях выходных столбцов компонентов, находящихся выше данного компонента в потоке данных. Например, если в выходе исходного компонента предоставлены три столбца, и следующий компонент вводит дополнительный выходной столбец, буфер для компонента назначения содержит четыре столбца, даже если компонент назначения будет записывать только два столбца.  
  
 Порядок столбцов во входном буфере не определяется индексом столбца в коллекции входных столбцов компонента назначения. Столбцы можно с гарантией обнаружить в строке буфера только с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> объекта <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>. Этот метод находит в указанном буфере столбец с указанным идентификатором и возвращает сведения о его расположении в строке. Обычно поиск индексов входных столбцов осуществляется в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, после чего они кэшируются разработчиком для последующего использования в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
 В следующем примере кода производится поиск входных столбцов в буфере в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> и сохранение сведений об их расположении в массиве. Впоследствии этот массив используется в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> для считывания значений столбцов из буфера.  
  
```csharp  
int[] cols;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
  
    cols = new int[input.InputColumnCollection.Count];  
  
    for (int x = 0; x < input.InputColumnCollection.Count; x++)  
    {  
        cols[x] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[x].LineageID);  
    }  
}  
```  
  
```vb  
Private cols As Integer()  
  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
    ReDim cols(input.InputColumnCollection.Count)  
  
    For x As Integer = 0 To input.InputColumnCollection.Count  
  
        cols(x) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(x).LineageID)  
    Next x  
  
End Sub  
```  
  
### <a name="processing-rows"></a>Обработка строк  
 После того как входные столбцы обнаружены в буфере, их можно считывать и записывать во внешний источник данных.  
  
 Когда компонент назначения записывает строки во внешний источник данных, можно обновить счетчики производительности «Прочитано строк» и «Прочитано байт из BLOB» путем вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A>. Дополнительные сведения см. в статье [Performance Counters](../../integration-services/performance/performance-counters.md).  
  
 В следующем примере показан компонент, который считывает строки из буфера, возвращаемого методом <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>. Индексы столбцов в буфере были найдены методом <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> из предыдущего примера кода.  
  
```csharp  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
        while (buffer.NextRow())  
        {  
            foreach (int col in cols)  
            {  
                if (!buffer.IsNull(col))  
                {  
                    //  TODO: Read the column data.  
                }  
            }  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For Each col As Integer In cols  
  
                If buffer.IsNull(col) = False Then  
  
                    '  TODO: Read the column data.  
                End If  
  
            Next col  
        End While  
End Sub  
```  
  
## <a name="sample"></a>Образец  
 В следующем образце показан простой компонент назначения, который использует диспетчер соединения файлов для сохранения в файлах двоичных данных из потока данных. В этом образце показаны не все методы и возможности, описанные в данном разделе. Он демонстрирует важные методы, которые должен переопределить любой пользовательский компонент назначения, однако не содержит кода для проверки во время разработки.  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace BlobDst  
{  
  [DtsPipelineComponent(DisplayName = "BLOB Extractor Destination", Description = "Writes values of BLOB columns to files")]  
  public class BlobDst : PipelineComponent  
  {  
    string m_DestDir;  
    int m_FileNameColumnIndex = -1;  
    int m_BlobColumnIndex = -1;  
  
    public override void ProvideComponentProperties()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection.New();  
      input.Name = "BLOB Extractor Destination Input";  
      input.HasSideEffects = true;  
  
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();  
      conn.Name = "FileConnection";  
    }  
  
    public override void AcquireConnections(object transaction)  
    {  
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];  
      m_DestDir = (string)conn.ConnectionManager.AcquireConnection(null);  
  
      if (m_DestDir.Length > 0 && m_DestDir[m_DestDir.Length - 1] != '\\')  
        m_DestDir += "\\";  
    }  
  
    public override IDTSInputColumn100 SetUsageType(int inputID, IDTSVirtualInput100 virtualInput, int lineageID, DTSUsageType usageType)  
    {  
      IDTSInputColumn100 inputColumn = base.SetUsageType(inputID, virtualInput, lineageID, usageType);  
      IDTSCustomProperty100 custProp;  
  
      custProp = inputColumn.CustomPropertyCollection.New();  
      custProp.Name = "IsFileName";  
      custProp.Value = (object)false;  
  
      custProp = inputColumn.CustomPropertyCollection.New();  
      custProp.Name = "IsBLOB";  
      custProp.Value = (object)false;  
  
      return inputColumn;  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
      IDTSCustomProperty100 custProp;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        custProp = column.CustomPropertyCollection["IsFileName"];  
        if ((bool)custProp.Value == true)  
        {  
          m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);  
        }  
  
        custProp = column.CustomPropertyCollection["IsBLOB"];  
        if ((bool)custProp.Value == true)  
        {  
          m_BlobColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        string strFileName = buffer.GetString(m_FileNameColumnIndex);  
        int blobLength = (int)buffer.GetBlobLength(m_BlobColumnIndex);  
        byte[] blobData = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength);  
  
        strFileName = TranslateFileName(strFileName);  
  
        // Make sure directory exists before creating file.  
        FileInfo fi = new FileInfo(strFileName);  
        if (!fi.Directory.Exists)  
          fi.Directory.Create();  
  
        // Write the data to the file.  
        FileStream fs = new FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None);  
        fs.Write(blobData, 0, blobLength);  
        fs.Close();  
      }  
    }  
  
    private string TranslateFileName(string fileName)  
    {  
      if (fileName.Length > 2 && fileName[1] == ':')  
        return m_DestDir + fileName.Substring(3, fileName.Length - 3);  
      else  
        return m_DestDir + fileName;  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.IO   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Namespace BlobDst   
  
 <DtsPipelineComponent(DisplayName="BLOB Extractor Destination", Description="Writes values of BLOB columns to files")> _   
 Public Class BlobDst   
 Inherits PipelineComponent   
   Private m_DestDir As String   
   Private m_FileNameColumnIndex As Integer = -1   
   Private m_BlobColumnIndex As Integer = -1   
  
   Public  Overrides Sub ProvideComponentProperties()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New   
     input.Name = "BLOB Extractor Destination Input"   
     input.HasSideEffects = True   
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New   
     conn.Name = "FileConnection"   
   End Sub   
  
   Public  Overrides Sub AcquireConnections(ByVal transaction As Object)   
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0)   
     m_DestDir = CType(conn.ConnectionManager.AcquireConnection(Nothing), String)   
     If m_DestDir.Length > 0 AndAlso Not (m_DestDir(m_DestDir.Length - 1) = "\"C) Then   
       m_DestDir += "\"   
     End If   
   End Sub   
  
   Public  Overrides Function SetUsageType(ByVal inputID As Integer, ByVal virtualInput As IDTSVirtualInput100, ByVal lineageID As Integer, ByVal usageType As DTSUsageType) As IDTSInputColumn100   
     Dim inputColumn As IDTSInputColumn100 = MyBase.SetUsageType(inputID, virtualInput, lineageID, usageType)   
     Dim custProp As IDTSCustomProperty100   
     custProp = inputColumn.CustomPropertyCollection.New   
     custProp.Name = "IsFileName"   
     custProp.Value = CType(False, Object)   
     custProp = inputColumn.CustomPropertyCollection.New   
     custProp.Name = "IsBLOB"   
     custProp.Value = CType(False, Object)   
     Return inputColumn   
   End Function   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     Dim custProp As IDTSCustomProperty100   
     For Each column As IDTSInputColumn100 In inputColumns   
       custProp = column.CustomPropertyCollection("IsFileName")   
       If CType(custProp.Value, Boolean) = True Then   
         m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer)   
       End If   
       custProp = column.CustomPropertyCollection("IsBLOB")   
       If CType(custProp.Value, Boolean) = True Then   
         m_BlobColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer)   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       Dim strFileName As String = buffer.GetString(m_FileNameColumnIndex)   
       Dim blobLength As Integer = CType(buffer.GetBlobLength(m_BlobColumnIndex), Integer)   
       Dim blobData As Byte() = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength)   
       strFileName = TranslateFileName(strFileName)   
       Dim fi As FileInfo = New FileInfo(strFileName)   
       ' Make sure directory exists before creating file.  
       If Not fi.Directory.Exists Then   
         fi.Directory.Create   
       End If   
       ' Write the data to the file.  
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None)   
       fs.Write(blobData, 0, blobLength)   
       fs.Close   
     End While   
   End Sub   
  
   Private Function TranslateFileName(ByVal fileName As String) As String   
     If fileName.Length > 2 AndAlso fileName(1) = ":"C Then   
       Return m_DestDir + fileName.Substring(3, fileName.Length - 3)   
     Else   
       Return m_DestDir + fileName   
     End If   
   End Function   
 End Class   
End Namespace  
```  
  
## <a name="see-also"></a>См. также  
 [Разработка пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)   
 [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
