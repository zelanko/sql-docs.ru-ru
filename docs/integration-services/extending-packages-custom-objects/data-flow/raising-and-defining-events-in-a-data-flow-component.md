---
title: "Компонент потока вызов и определение событий в элементе данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a900b27c9056d95fb2284d8ba9d6b09d9c6635b5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Вызов и определение событий в компоненте потока данных
  Разработчики компонентов могут создавать подмножество событий, определенных в интерфейсе <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>, вызывая методы, доступ к которым определяется свойством <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Можно также определять пользовательские события, используя коллекцию <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>, и создавать эти события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. В данном разделе описывается разработка и вызов событий, а также содержатся рекомендации по вызову событий во время разработки.  
  
## <a name="raising-events"></a>Вызов событий  
 Компоненты вызывают события с помощью **пожара\<X >** методы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> интерфейса. События можно вызывать во время разработки и во время выполнения компонента. Обычно во время разработки методы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> вызываются в процессе проверки компонента. Эти события выводят сообщения на **список ошибок** области [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] и предоставить отзыв пользователям компонента, если компонент настроен неправильно.  
  
 Компоненты могут также вызывать события в любой момент во время выполнения. События позволяют разработчикам компонента предоставлять отзыв пользователям компонента в процессе его работы. Вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> во время выполнения, скорее всего, приведет к аварийному завершению работы всего пакета.  
  
## <a name="defining-and-raising-custom-events"></a>Определение и вызов пользовательских событий  
  
### <a name="defining-a-custom-event"></a>Разработка пользовательского события  
 Пользовательские события создаются с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>. Эта коллекция создается задачей потока данных и предоставляется разработчику компонента как свойство через базовый класс <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Этот класс содержит пользовательские события, определенные задачей потока данных, и пользовательские события, определенные компонентом с помощью вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.  
  
 Пользовательские события компонента не сохраняются в коде XML пакета. Поэтому метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> вызывается и во время разработки, и во время выполнения, чтобы компонент мог определить события, которые вызывает.  
  
 *Значением переменой allowEventHandlers* параметр <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> метод указывает, допускает ли компонент <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> объекты должны быть созданы для события. Следует заметить, что объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> являются синхронными. Поэтому компонент не возобновляет выполнение, пока объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>, принадлежащий пользовательскому событию, не закончил работу. Если *значением переменой allowEventHandlers* параметр **true**, каждый параметр события автоматически становится доступным для любого <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> объектов с помощью переменных, которые создаются и заполняются автоматически [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] среды выполнения.  
  
### <a name="raising-a-custom-event"></a>Вызов пользовательского события  
 Компоненты вызывают пользовательские события с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>, передавая ему имя, текст и параметры события. Если *значением переменой allowEventHandlers* параметр **true**, любые <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> , созданные для пользовательского события, выполняются командой [!INCLUDE[ssIS](../../../includes/ssis-md.md)] механизм среды выполнения.  
  
### <a name="custom-event-sample"></a>Образец пользовательского события  
 Следующий пример кода демонстрирует компонент, который определяет пользовательское событие с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>, а затем вызывает это событие во время выполнения с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.  
  
```csharp  
public override void RegisterEvents()  
{  
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};  
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};  
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};  
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref paramterTypes, ref parameterDescriptions);  
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
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, paramterTypes, parameterDescriptions)   
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
 [Службы Integration Services &#40; Службы SSIS &#41; Обработчики событий](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Добавить обработчик событий в пакет](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  

