---
title: "Мониторинг служб Analysis Services с помощью расширенных событий SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- XEvents
- Sql13.ssms.XeASNewEventSession.General.f1
- Sql13.ssms.XeASNewEventSession.Events.f1
- Sql13.ssms.XeASNewEventSession.Targets.f1
- Sql13.ssms.XeASNewEventSession.Advanced.f1
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cec6da660c202dfde5a1169dd34397fca5c51207
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="monitor-analysis-services-with-sql-server-extended-events"></a>Мониторинг служб Analysis Services с помощью расширенных событий SQL Server
  Расширенные события (*xEvents*) — это упрощенная система трассировки и мониторинга производительности, которая использует очень небольшое количество системных ресурсов. Это делает систему идеальным средством для диагностики проблем как на производственных, так и на тестовых серверах. Система также характеризуется высокой масштабируемостью и возможностями настройки. В SQL Server 2016 ее использование упрощено благодаря поддержке новых встроенных средств. В SQL Server Management Studio для подключений к экземплярам служб Analysis Services можно настроить, запустить и отслеживать динамическую трассировку так же, как и при использовании приложения SQL Server Profiler. Добавление улучшенных средств не только делает xEvents более рациональной заменой SQL Server Profiler, но и позволяет упорядочить диагностику проблем в ядре СУБД и рабочих нагрузках служб Analysis Services.  
  
 Кроме использования [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]вы также можете настроить сеансы расширенных событий  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] традиционным способом — с помощью скриптов XMLA, поддерживаемых в предыдущих выпусках.  
  
 Все события служб Analysis Services можно регистрировать и направлять конкретным получателям, как определено в [расширенных событиях](../../relational-databases/extended-events/extended-events.md).  
  
> [!NOTE]  
>  Просмотрите это [краткое вводное видео](https://www.youtube.com/watch?v=ja2mOHWRVC0&index=1&list=PLv2BtOtLblH1YvzQ5YnjfQFr_oKEvMk19) или прочитайте [публикацию в блоге службы поддержки](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx) , чтобы узнать больше о расширенных событиях xEvents для служб Analysis Services в SQL Server 2016.  
  
##  <a name="bkmk_top"></a> В этом разделе  
  
-   [Настройка служб Analysis Services с помощью Management Studio](#bkmk_ssas_extended_events_ssms)  
  
-   [Скрипт XMLA для запуска расширенных событий в службах Analysis Services](#bkmk_script_start)  
  
##  <a name="bkmk_ssas_extended_events_ssms"></a> Настройка служб Analysis Services с помощью Management Studio  
 Как для табличных, так и для многомерных экземпляров Management Studio предусматривает новую папку "Управление", содержащую инициированные пользователем сеансы xEvent. Одновременно можно запускать несколько сеансов. Однако в текущей реализации пользовательский интерфейс расширенных событий [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживает обновление или воспроизведение существующего сеанса.  
  
 ![ssas_extended_events_ssms_start](../../analysis-services/instances/media/ssas-extended-events-ssms-start.png "ssas_extended_events_ssms_start")  
  
 **Выбор событий**  
  
 Если вы уже знаете, какие события нужно зарегистрировать, проще всего добавить их в трассировку, выполнив поиск. В противном случае для мониторинга операций обычно используются следующие события:  
  
-   **CommandBegin** и **CommandEnd**.  
  
-   **QueryBegin**, **QueryEnd**и **QuerySubcubeVerbose** (показывает весь запрос MDX или DAX, отправляемый на сервер), а также **ResourceUsage** для статистики по ресурсам, потребленным запросом, и количеству возвращенных строк.  
  
-   **ProgressReportBegin** и **ProgressReportEnd** (для операций обработки).  
  
-   **AuditLogin** и **AuditLogout** (фиксирует идентификатор пользователя, под которым клиентское приложение подключается к службам Analysis Services).  
  
 **Выбор хранилища данных**  
  
 Сеанс может передаваться в виде потока в окно Management Studio или сохраняться в файл для последующего анализа с помощью Power Query или Excel.  
  
-   **event_file** сохраняет данные сеанса в XEL-файле.  
  
-   **event_stream** включает параметр **Просмотр данных, передаваемых в режиме реального времени** в среде Management Studio.  
  
-   **ring_buffer** сохраняет данные сеанса в памяти, пока работает сервер. При перезапуске сервера данные сеанса теряются.  
  
 **Добавление полей событий**  
  
 Не забудьте при настройке сеанса включить поля событий, чтобы можно было легко просматривать сведения, представляющие интерес.  
  
 Параметр**Настроить** находится в удаленной области диалогового окна.  
  
 ![Настройка SSAS xevents](../../analysis-services/instances/media/ssas-xevents-configure.PNG "Настройка ssas xevents")  
  
 В конфигурации на вкладке "Поля событий" выберите поле **TextData** , чтобы оно отображалось рядом с событием и показывало возвращаемые значения, включая запросы, которые выполняются на сервере.  
  
 После настройки сеанса для нужных событий и хранения данных можно, нажав кнопку сценария, отправить конфигурацию в одно из поддерживаемых целевых расположений: файл, новый запрос в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и буфер обмена.  
  
 **Обновление сеансов**  
  
 После создания сеанса не забудьте обновить папку "Сеансы" в Management Studio для просмотра сеанса, который вы только что создали. Если вы настроили event_stream, можно щелкнуть правой кнопкой мыши имя сеанса и выбрать **Просмотр динамических данных** для мониторинга активности сервера в режиме реального времени.  
  
##  <a name="bkmk_script_start"></a> Скрипт XMLA для запуска расширенных событий в службах Analysis Services  
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
 Событие служб Analysis Services, к которому должен быть предоставлен доступ. Имена событий см. в разделе [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md) .  
  
 *data_filename*  
 Имя файла данных, который содержит данные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
 *metadata_filename*  
 Имя файла данных, который содержит метаданные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
||  
|-|  
|![Значок стрелки, используемый с обратно к верхней](../../analysis-services/instances/media/uparrow16x16.gif "значок стрелки, используемый с обратно к верхней") [в этом разделе](#bkmk_top)|  
  
##  <a name="bkmk_script_stop"></a> Скрипт XMLA для остановки расширенных событий в службах Analysis Services  
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
  
||  
|-|  
|![Значок стрелки, используемый с обратно к верхней](../../analysis-services/instances/media/uparrow16x16.gif "значок стрелки, используемый с обратно к верхней") [в этом разделе](#bkmk_top)|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  

