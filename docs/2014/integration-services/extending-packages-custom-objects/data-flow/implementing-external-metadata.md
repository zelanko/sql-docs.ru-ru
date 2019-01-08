---
title: Реализация внешних метаданных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d7eaa0deb17812bbf7d1da4717d24a1fdfb4dadf
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362216"
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
 Если компонент подключен к внешнему источнику данных, столбцы во входной или выходной коллекции проверяются непосредственно по внешнему источнику данных. Кроме того, необходимо выполнить проверку в отношении столбцов в коллекции внешних метаданных. Она необходима, так как коллекцию внешних метаданных можно изменить с помощью **расширенного редактора** в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], а изменения коллекции не обнаруживаются. Поэтому в подключенном состоянии компоненты должны гарантировать соответствие коллекции столбцов внешних метаданных столбцам во внешнем источнике данных.  
  
 Вы можете скрыть коллекции внешних метаданных в **расширенный редактор** , задав <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> свойство коллекции `false`. Однако при этом также скрывается вкладка **Сопоставление столбцов** редактора, которая позволяет пользователям сопоставлять столбцы из входной или выходной коллекции столбцам коллекции столбцов внешних метаданных. Значение `false` этого свойства не мешает разработчиками программно изменять коллекцию, но оно обеспечивает уровень защиты коллекции столбцов внешних метаданных для компонента, который используется исключительно в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="disconnected-validation"></a>Проверка с отключением  
 Если компонент отключен от внешнего источника данных, проверка упрощается, поскольку столбцы во входной или выходной коллекции проверяются по коллекции внешних метаданных, а не по внешнему источнику данных. Компонент должен выполнять проверку с отключением, если не установлено соединение с внешним источником данных или если свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> имеет значение `false`.  
  
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
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../data-flow/data-flow.md)  
  
  
