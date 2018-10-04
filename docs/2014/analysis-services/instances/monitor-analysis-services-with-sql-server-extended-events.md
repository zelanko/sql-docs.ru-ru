---
title: Использовать расширенные события (XEvents) SQL Server для мониторинга служб Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5716541be57191cd6bb3e6e6399a354889b2cf58
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179674"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a>Использование расширенных событий SQL Server (XEvents) для мониторинга служб Analysis Services
  Службы Analysis Services предоставляют возможности трассировки посредством использования [расширенных событий](../../relational-databases/extended-events/extended-events.md).  
  
 Расширенные события — это инфраструктура событий с высоким уровнем масштабирования и настройки для серверных систем. Расширенные события — это упрощенная система мониторинга производительности, в которой применяется очень небольшой объем ресурсов.  
  
 Все службы Analysis Services, события могут записываться и направлены к конкретным получателям, как определено в [расширенных событий](../../relational-databases/extended-events/extended-events.md), через XEvents.  
  
## <a name="initiating-extended-events-in-analysis-services"></a>Запуск расширенных событий в службах Analysis Services  
 Расширенная трассировка событий включается с помощью команды скрипта создания объекта, аналогичной команде XML для аналитики, как показано ниже.  
  
```  
<Execute …>  
   <Command>  
      <Batch …>  
         <Create …>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session …>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" …/>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Следующие элементы должны быть определены пользователем с учетом потребностей трассировки:  
  
 *trace_id*  
 Определяет уникальный идентификатор для данной трассировки.  
  
 *trace_name*  
 Имя, присвоенное данной трассировке. Как правило, понятное определение трассировки. Обычно принято использовать в качестве имени значение *trace_id* .  
  
 *AS_event*  
 Событие служб Analysis Services, к которому должен быть предоставлен доступ. Имена событий см. в разделе [События трассировки служб Analysis Services](../trace-events/analysis-services-trace-events.md) .  
  
 *data_filename*  
 Имя файла данных, который содержит данные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
 *metadata_filename*  
 Имя файла данных, который содержит метаданные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
## <a name="stopping-extended-events-in-analysis-services"></a>Останов расширенных событий в службах Analysis Services  
 Чтобы остановить объект расширенных событий трассировки, необходимо удалить этот объект с помощью команды скрипта удаления объекта, аналогичной применяемой в XML для аналитики, как показано ниже.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch …>  
         <Delete …>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Следующие элементы должны быть определены пользователем с учетом потребностей трассировки:  
  
 *trace_id*  
 Определяет уникальный идентификатор удаляемой трассировки.  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
