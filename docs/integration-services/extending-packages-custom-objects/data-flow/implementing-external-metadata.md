---
title: "Реализация внешних метаданных | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96d413bca20ec171d515ac6d0ad81b5b994bd854
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-external-metadata"></a>Реализация внешних метаданных
  Если компонент отключен от источника данных, можно выполнить проверку столбцов во входных и выходных коллекциях столбцов относительно внешнего источника данных с помощью интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100>. Он позволяет сохранять моментальный снимок столбцов внешнего источника данных и сопоставлять эти столбцы со столбцами входных и выходных коллекций столбцов компонента.  
  
 Реализация столбцов внешних метаданных добавляет издержки и сложности при разработке компонента, поскольку необходимо хранить дополнительную коллекцию столбцов и выполнять их проверку, но возможность избежать затратных обращений к серверу во время проверки может оправдать такую разработку.  
  
## <a name="populating-external-metadata-columns"></a>Заполнение столбцов внешних метаданных  
 Столбцы внешних метаданных обычно добавляются к коллекции, если создан соответствующий входной или выходной столбец. Новые столбцы создаются вызовом метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A>. Затем устанавливаются свойства столбца, чтобы соответствовать внешнему источнику данных.  
  
 Столбец внешних метаданных сопоставляется с соответствующим входным или выходным столбцом путем присвоения идентификатора столбца внешних метаданных свойству <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> входного или выходного столбца. Это позволяет легко обнаружить столбец внешних метаданных для конкретного входного или выходного столбца с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> коллекции.  
  
 В следующем примере показано создание столбца внешних метаданных и его сопоставление с выходным столбцом с помощью установки свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A>.  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a>Проверка с помощью столбцов внешних метаданных  
 Проверка требует дополнительных шагов для компонента, хранящего коллекцию столбцов внешних метаданных, поскольку проверку необходимо выполнять относительно дополнительной коллекции столбцов. Проверку можно разделить на проверку с подключением и проверку с отключением.  
  
### <a name="connected-validation"></a>Проверка с подключением  
 Если компонент подключен к внешнему источнику данных, столбцы во входной или выходной коллекции проверяются непосредственно по внешнему источнику данных. Кроме того, необходимо выполнить проверку в отношении столбцов в коллекции внешних метаданных. Это необходимо, так как коллекция внешних метаданных можно изменить с помощью **расширенный редактор** в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], и изменения, внесенные в коллекцию, не обнаруживаются. Поэтому в подключенном состоянии компоненты должны гарантировать соответствие коллекции столбцов внешних метаданных столбцам во внешнем источнике данных.  
  
 Вы можете скрыть коллекция внешних метаданных в **расширенный редактор** , установив <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> свойства коллекции для **false**. Однако при этом также скрывается **сопоставление столбцов** редактора, которая позволяет пользователям сопоставлять столбцы из входной или выходной коллекции столбцам коллекции столбцов внешних метаданных. Присвоение этому свойству **false** не мешает разработчиками программно изменять коллекцию, но он обеспечивает уровень защиты коллекции столбцов внешних метаданных компонента, который используется исключительно в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="disconnected-validation"></a>Проверка с отключением  
 Если компонент отключен от внешнего источника данных, проверка упрощается, поскольку столбцы во входной или выходной коллекции проверяются по коллекции внешних метаданных, а не по внешнему источнику данных. Компонент должен выполнять проверку с отключением, если не было установлено подключение к внешнему источнику данных или <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> свойство **false**.  
  
 В следующем примере кода показана реализация компонента, выполняющего проверку подлинности по коллекции столбцов внешних метаданных.  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  

## <a name="see-also"></a>См. также:  
 [Поток данных](../../../integration-services/data-flow/data-flow.md)  
  
  

