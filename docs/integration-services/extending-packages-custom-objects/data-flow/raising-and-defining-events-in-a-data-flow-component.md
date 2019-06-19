---
title: Вызов и определение событий в компоненте потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ee44d80d0600f402c317c2432fc7c9eb5105015e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65724681"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Вызов и определение событий в компоненте потока данных

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Разработчики компонентов могут создавать подмножество событий, определенных в интерфейсе <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>, вызывая методы, доступ к которым определяется свойством <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Можно также определять пользовательские события, используя коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>, и создавать эти события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. В данном разделе описывается разработка и вызов событий, а также содержатся рекомендации по вызову событий во время разработки.  
  
## <a name="raising-events"></a>Вызов событий  
 Компоненты вызывают события с помощью методов **Fire\<X>** интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. События можно вызывать во время разработки и во время выполнения компонента. Обычно во время разработки методы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> вызываются в процессе проверки компонента. Эти события выводят сообщения на панели **Список ошибок** среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] и обеспечивают отзыв для пользователей компонента в случаях, когда он неправильно настроен.  
  
 Компоненты могут также вызывать события в любой момент во время выполнения. События позволяют разработчикам компонента предоставлять отзыв пользователям компонента в процессе его работы. Вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> во время выполнения, скорее всего, приведет к аварийному завершению работы всего пакета.  
  
## <a name="defining-and-raising-custom-events"></a>Определение и вызов пользовательских событий  
  
### <a name="defining-a-custom-event"></a>Разработка пользовательского события  
 Пользовательские события создаются с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>. Эта коллекция создается задачей потока данных и предоставляется разработчику компонента как свойство через базовый класс <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Этот класс содержит пользовательские события, определенные задачей потока данных, и пользовательские события, определенные компонентом с помощью вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.  
  
 Пользовательские события компонента не сохраняются в коде XML пакета. Поэтому метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> вызывается и во время разработки, и во время выполнения, чтобы компонент мог определить события, которые вызывает.  
  
 Параметр *allowEventHandlers* метода <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> указывает, позволяет ли компонент создавать для этого события объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>. Следует заметить, что объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> являются синхронными. Поэтому компонент не возобновляет выполнение, пока объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>, принадлежащий пользовательскому событию, не закончил работу. Если параметр *allowEventHandlers* равен **true**, все параметры события автоматически доступны всем объектам <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> через переменные, созданные и заполняемые автоматически службами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] во время выполнения.  
  
### <a name="raising-a-custom-event"></a>Вызов пользовательского события  
 Компоненты вызывают пользовательские события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>, передавая ему имя, текст и параметры события. Если параметр *allowEventHandlers* равен **true**, все объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers>, созданные для пользовательского события, выполняются подсистемой выполнения служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
### <a name="custom-event-sample"></a>Образец пользовательского события  
 Следующий пример кода демонстрирует компонент, который определяет пользовательское событие с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>, а затем вызывает это событие во время выполнения с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.  
  
```csharp  
public override void RegisterEvents()  
{  
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};  
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};  
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};  
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);  
}  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
    while (buffer.NextRow())  
    {  
       // Process buffer rows.  
    }  
  
    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];  
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };  
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);  
}  
```  
  
```vb  
Public  Overrides Sub RegisterEvents()   
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"}   
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)}   
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."}   
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions)   
End Sub   
  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
  While buffer.NextRow   
  End While   
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort")   
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now}   
  ComponentMetaData.FireCustomEvent("StartingSort", _  
    "Beginning sort operation.", arguments, _  
    ComponentMetaData.Name, FireSortEventAgain)   
End Sub  
```  

## <a name="see-also"></a>См. также:  
 [Обработчики событий в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Добавление обработчика событий к пакету](https://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
