---
title: Используйте SQL Server Profiler для создания набора элементов сбора трассировки SQL (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace collector set
ms.assetid: b6941dc0-50f5-475d-82eb-ce7c68117489
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 06e4e89e974476f2864b219f6030110afc213470
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43806770"
---
# <a name="use-sql-server-profiler-to-create-a-sql-trace-collection-set-sql-server-management-studio"></a>Использование приложения SQL Server Profiler для создания набора элементов сбора трассировки SQL (среда SQL Server Management Studio)
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно использовать возможности серверной трассировки приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], чтобы экспортировать определение трассировки для создания набора элементов сбора, использующего общий тип сборщика трассировки SQL. Этот процесс состоит из двух частей.  
  
1.  Создание и экспорт трассировки приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
2.  Создание скрипта нового набора сбора на основе экспортированной трассировки.  
  
 Сценарий следующих процедур включает сбор данных о любой хранимой процедуре, требующей для выполнения 80 миллисекунд и более. Для выполнения этих процедур необходимо уметь следующее.  
  
-   Использовать приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для создания и настройки трассировки.  
  
-   Использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для открытия, изменения и выполнения запроса.  
  
### <a name="create-and-export-a-sql-server-profiler-trace"></a>Создание и экспорт трассировки приложения SQL Server Profiler  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. (В меню **Инструменты** выберите приложение **SQL Server Profiler**.)  
  
2.  В диалоговом окне **Соединения с сервером** нажмите кнопку **Отмена**.  
  
3.  В данном случае убедитесь, что настроено отображение значений продолжительности в миллисекундах (по умолчанию). Для этого выполните следующие шаги.  
  
    1.  В меню **Сервис** выберите команду **Параметры**.  
  
    2.  Убедитесь, что в области **Параметры отображения** флажок «Показывать значения в столбце "Продолжительность" в микросекундах» не установлен.  
  
    3.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Общие параметры** .  
  
4.  В меню **Файл** выберите **Создать трассировку**.  
  
5.  В диалоговом окне **Подключение к серверу** выберите нужный сервер и нажмите кнопку **Соединить**.  
  
     отображается диалоговое окно **Свойства трассировки** .  
  
6.  На вкладке **Общие** выполните следующее.  
  
    1.  В поле **Имя трассировки** введите требуемое имя трассировки. В этом примере является имя трассировки `SPgt80`.  
  
    2.  В списке **Использовать шаблон**выберите шаблон для трассировки. В этом примере выберите **TSQL_SPs**.  
  
7.  На вкладке **Выбор событий** выполните следующие действия.  
  
    1.  Определите события для трассировки. Например, снимите все флажки в столбце **События** , кроме **ExistingConnection** и **SP:Completed**.  
  
    2.  В правом нижнем углу установите флажок **Показать все столбцы** .  
  
    3.  Щелкните строку **SP:Completed** .  
  
    4.  Прокрутите строку до столбца **Продолжительность** и установите флажок **Продолжительность** .  
  
8.  В правом нижнем углу щелкните **Фильтры столбцов** . Откроется диалоговое окно **Изменение фильтра** . В окне **Изменение фильтра** выполните следующие действия.  
  
    1.  В списке фильтров выберите **Продолжительность:**.  
  
    2.  В окне логического оператора разверните **больше или равно** узла, тип `80` как значение, а затем нажмите кнопку **ОК**.  
  
9. Чтобы запустить трассировку, нажмите кнопку **Выполнить** .  
  
10. На панели инструментов щелкните **Остановить выбранную трассировку** или **Приостановить выбранную трассировку**.  
  
11. В меню **Файл** укажите пункт **Экспорт**, затем **Создать определение трассировки**и щелкните **Для набора элементов сбора трассировки SQL**.  
  
12. В диалоговом окне **Сохранить как** введите имя определения трассировки в поле **Имя файла** и сохраните файл в требуемом расположении. В данном примере имя файла совпадает с именем трассировки (SPgt80).  
  
13. Нажмите кнопку **ОК** при появлении сообщения об успешном сохранении файла и закройте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="script-a-new-collection-set-from-a-sql-server-profiler-trace"></a>Создание скрипта нового набора элементов сбора из трассировки приложения SQL Server Profiler  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Файл** выберите команду **Открыть** , а затем **Файл**.  
  
2.  В диалоговом окне **Открытие файла** найдите и откройте файл, созданный в предыдущей процедуре (SPgt80).  
  
     Сохраненная информация о трассировке открывается в окне «Запрос» и объединяется в скрипт, который можно запустить для создания новых наборов элементов сбора.  
  
3.  Прокрутите скрипт и выполните следующие замены, отмеченные в текстовом комментарии скрипта.  
  
    -   Замените строку **Имя набора сбора SQLTrace** именем, которое будет использоваться для набора элементов сбора. В этом примере имя набора элементов сбора `SPROC_CollectionSet`.  
  
    -   Замените строку **Имя элемента сбора SQLTrace** именем, которое будет использоваться для элемента сбора. В этом примере имя элемента сбора `SPROC_Collection_Item`.  
  
4.  Нажмите кнопку **Выполнить** , чтобы запустить запрос и создать набор элементов сбора.  
  
5.  В обозревателе объектов проверьте успешность создания набора элементов сбора. Для этого выполните следующие шаги.  
  
    1.  Щелкните правой кнопкой мыши узел **Управление**и выберите команду **Обновить**.  
  
    2.  Разверните узел **Управление**, затем **Сбор данных**.  
  
     `SPROC_CollectionSet` Отображается набор элементов сбора на том же уровне, что **System Data Collection Sets** узла. По умолчанию этот набор элементов сбора отключен.  
  
6.  С помощью обозревателя объектов измените свойства набора SPROC_CollectionSet, например режим сбора и расписание передачи. Остальные действия аналогичны тем, что выполнялись бы с наборами сбора системных данных, поставляемыми в составе поставщика данных.  
  
## <a name="example"></a>Пример  
 Следующий образец кода содержит скрипт, созданный в результате выполнения шагов, описанных в предыдущих процедурах.  
  
```  
/*************************************************************/  
-- SQL Trace collection set generated from SQL Server Profiler  
-- Date: 11/19/2007  12:55:31 AM  
/*************************************************************/  
  
USE msdb  
GO  
  
BEGIN TRANSACTION  
BEGIN TRY  
  
-- Define collection set  
-- ***  
-- *** Replace 'SqlTrace Collection Set Name Here' in the   
-- *** following script with the name you want  
-- *** to use for the collection set.  
-- ***  
DECLARE @collection_set_id int;  
EXEC [dbo].[sp_syscollector_create_collection_set]  
    @name = N'SPROC_CollectionSet',  
    @schedule_name = N'CollectorSchedule_Every_15min',  
    @collection_mode = 0, -- cached mode needed for Trace collections  
    @logging_level = 0, -- minimum logging  
    @days_until_expiration = 5,  
    @description = N'Collection set generated by SQL Server Profiler',  
    @collection_set_id = @collection_set_id output;  
SELECT @collection_set_id;  
  
-- Define input and output variables for the collection item.  
DECLARE @trace_definition xml;  
DECLARE @collection_item_id int;  
  
-- Define the trace parameters as an XML variable  
SELECT @trace_definition = convert(xml,   
N'<ns:SqlTraceCollector xmlns:ns"DataCollectorType" use_default="0">  
<Events>  
  <EventType name="Sessions">  
    <Event id="17" name="ExistingConnection" columnslist="1,2,14,26,3,35,12" />  
  </EventType>  
  <EventType name="Stored Procedures">  
    <Event id="43" name="SP:Completed" columnslist="1,2,26,34,3,35,12,13,14,22" />  
  </EventType>  
</Events>  
<Filters>  
  <Filter columnid="13" columnname="Duration" logical_operator="AND" comparison_operator="GE" value="80000L" />  
</Filters>  
</ns:SqlTraceCollector>  
');  
  
-- Retrieve the collector type GUID for the trace collector type.  
DECLARE @collector_type_GUID uniqueidentifier;  
SELECT @collector_type_GUID = collector_type_uid FROM [dbo].[syscollector_collector_types] WHERE name = N'Generic SQL Trace Collector Type';  
  
-- Create the trace collection item.  
-- ***  
-- *** Replace 'SqlTrace Collection Item Name Here' in   
-- *** the following script with the name you want to  
-- *** use for the collection item.  
-- ***  
EXEC [dbo].[sp_syscollector_create_collection_item]  
   @collection_set_id = @collection_set_id,  
   @collector_type_uid = @collector_type_GUID,  
   @name = N'SPROC_Collection_Item',  
   @frequency = 900, -- specified the frequency for checking to see if trace is still running  
   @parameters = @trace_definition,  
   @collection_item_id = @collection_item_id output;  
SELECT @collection_item_id;  
  
COMMIT TRANSACTION;  
END TRY  
  
BEGIN CATCH  
ROLLBACK TRANSACTION;  
DECLARE @ErrorMessage nvarchar(4000);  
DECLARE @ErrorSeverity int;  
DECLARE @ErrorState int;  
DECLARE @ErrorNumber int;  
DECLARE @ErrorLine int;  
DECLARE @ErrorProcedure nvarchar(200);  
SELECT @ErrorLine = ERROR_LINE(),  
       @ErrorSeverity = ERROR_SEVERITY(),  
       @ErrorState = ERROR_STATE(),  
       @ErrorNumber = ERROR_NUMBER(),  
       @ErrorMessage = ERROR_MESSAGE(),  
       @ErrorProcedure = ISNULL(ERROR_PROCEDURE(), '-');  
RAISERROR (14684, @ErrorSeverity, 1 , @ErrorNumber, @ErrorSeverity, @ErrorState, @ErrorProcedure, @ErrorLine, @ErrorMessage);  
END CATCH;  
GO  
```  
  
  
