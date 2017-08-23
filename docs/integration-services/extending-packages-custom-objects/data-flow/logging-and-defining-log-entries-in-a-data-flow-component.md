---
title: "Ведение журнала и определение элементов журнала в данные компонента потока | Документы Microsoft"
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
helpviewer_keywords:
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a0cbdbb818c7299221172f5ceb9b4ee5c54bddcb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a>Ведение журнала и определение элементов журнала в компоненте потока данных
  Пользовательские компоненты потока данных могут помещать сообщения в существующую запись журнала с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Они могут также предоставлять информацию для пользователя с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> или подобных методов интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Однако этот подход создает нагрузку по вызову и обработке дополнительных событий и заставляет пользователя фильтровать многочисленные информационные сообщения в поисках сообщений, которые могут представлять интерес. Можно использовать собственный формат записи журнала, как показано далее, для предоставления пользователям разработанного компонента точно обозначенной информации.  
  
## <a name="registering-and-using-a-custom-log-entry"></a>Регистрация и использование пользовательской записи журнала  
  
### <a name="registering-a-custom-log-entry"></a>Регистрация пользовательской записи журнала  
 Для регистрации пользовательской записи журнала, чтобы ее мог использовать разрабатываемый компонент, нужно переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. В следующем примере проводится регистрация пользовательской записи журнала и передается имя и описание.  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 Перечисление <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> подсказывает во время выполнения, как часто событие будет заноситься в журнал.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: событие заносится в журнал только иногда, но не во время каждого выполнения.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: событие заносится в журнал определенное количество раз во время каждого выполнения.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: событие заносится в журнал несколько раз пропорционально объему выполненной работы.  
  
 В приведенном выше примере используется значение <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>, поскольку ожидается, что компонент будет создавать запись в журнале один раз во время каждого выполнения.  
  
 После регистрации пользовательской записи журнала и добавления экземпляра пользовательского компонента в область конструктора данных потока, **ведение журнала** в конструкторе появится новая запись с именем «Мой собственный формат записи журнала» в списке доступных записей журнала.  
  
### <a name="logging-to-a-custom-log-entry"></a>Внесение в журнал пользовательской записи  
 После регистрации пользовательской записи журнала компонент может создавать такие записи в журнале. В приведенном ниже примере пользовательская запись журнала заносится в журнал во время работы метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, содержащего текст инструкции SQL, используемой компонентом.  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 Теперь, когда пользователь запустит пакет, выбрав «Мой настраиваемый компонент записи журнала» в **входа** диалоговое окно, журнал будет содержать запись, явно помеченная как «Пользователь::мой собственный формат записи журнала.» Новая запись в журнале содержит текст инструкции SQL, отметку времени и всю дополнительную информацию, заданную разработчиком.  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
