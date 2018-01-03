---
title: "Сохранение трассировок и шаблонов трассировок | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- exporting trace templates
- importing trace templates
- SQL Server Profiler, templates
ms.assetid: 957e6bf8-e7a3-4a59-a1cd-0a41538a8158
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e447a1b51919fcece9560a0d37cb5f526a615a3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="save-traces-and-trace-templates"></a>Сохранение трассировок и шаблонов трассировок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Важно различать сохранение файлов трассировки от сохранения шаблонов трассировок. Сохранение файла трассировки предполагает сохранение собранных данных о событиях в указанном месте. Сохранение шаблона трассировки связано с сохранением определения трассировки (например указанных столбцов данных, классов событий или фильтров).  
  
## <a name="saving-traces"></a>сохранение трассировок  
 Сохраняйте собранные данные о событиях в файле или таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если позднее нужно будет проанализировать или воспроизвести их. Используйте файл трассировки для решения следующих задач.  
  
-   Используйте файл или таблицу трассировки с целью создания рабочей нагрузки, применяемой в качестве входных данных для помощника по настройке ядра СУБД.  
  
-   Используйте файл трассировки для регистрации событий и отправки этих данных поставщику услуг поддержки с целью ее анализа.  
  
-   Используйте инструменты обработки запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для доступа к данным или просмотра данных в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Непосредственно обращаться к таблице трассировки могут только элементы предопределенной роли сервера **sysadmin** и создатель таблицы.  
  
> [!NOTE]  
>  Данные трассировки записываются в таблицу медленнее, чем в файл. Можно записать данные трассировки в файл, открыть его и сохранить трассировку в форме таблицы трассировки.  
  
 При использовании файла трассировки приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] сохраняет собранные данные о событиях (не определения трассировок) в файле трассировки [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] с расширением TRC (\*.trc). При сохранении файла трассировки это расширение автоматически добавляется к его имени независимо от любого другого указанного расширения. Например, если указать файл трассировки **Trace.dat**, созданный файл будет назван **Trace.dat.trc**.  
  
> [!IMPORTANT]  
>  Пользователи, которые имеют разрешение SHOWPLAN, ALTER TRACE или VIEW SERVER STATE, могут просматривать запросы, захваченные выходом Showplan. Эти запросы могут содержать конфиденциальные сведения, такие как пароли. В связи с этим рекомендуется предоставлять данные разрешения только пользователям, которые имеют право просмотра конфиденциальных данных, например членам предопределенной роли базы данных **db_owner** или членам предопределенной роли сервера **sysadmin** . Также рекомендуется сохранять файлы Showplan или файлы трассировки, содержащие события, связанные с инструкцией Showplan, только в каталог, расположенный в файловой системе NTFS, для которого есть возможность ограничить доступ, предоставляя его только пользователям, имеющим право просмотра конфиденциальных данных.  
  
## <a name="saving-templates"></a>Сохранение шаблонов  
 Определение шаблона трассировки включает классы событий, столбцы данных, фильтры и все прочие свойства (кроме перехватываемых данных событий), которые используются для создания трассировки. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] предоставляет стандартные системные шаблоны для общих задач трассировки и для конкретных задач, таких как создание нагрузки, которую помощник по настройке ядра СУБД может использовать для настройки физической структуры базы данных. Кроме того, можно создавать и сохранять пользовательские шаблоны.  
  
### <a name="importing-and-exporting-templates"></a>Импорт и экспорт шаблонов  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет импортировать и экспортировать шаблоны с одного сервера на другой. При экспорте шаблона копия существующего шаблона записывается в указанный каталог. При импорте создается копия указанного шаблона. Во время просмотра этих шаблонов в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]их можно отличить от системных шаблонов по слову «(user)», предшествующему имени шаблона. Переписать или непосредственно изменить предопределенный системный шаблон нельзя.  
  
### <a name="analyzing-performance-with-templates"></a>Анализ производительности при помощи шаблонов  
 Если часто инициируется мониторинг [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то нужно использовать для анализа производительности шаблоны. При этом каждый раз регистрируются одни и те же данные о событиях, и используется одно и то же определение трассировки для мониторинга тех же событий. Определять классы событий и столбцы данных при каждом создании трассировки не нужно. Кроме того, шаблон можно предоставить другому пользователю для мониторинга специфических событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, поставщик услуг поддержки может предоставить шаблон своему заказчику. Используя этот шаблон, заказчик может собрать необходимые данные о событиях и отправить их поставщику услуг поддержки для выполнения анализа.  
  
 **Сохранение трассировки в файле**  
  
 [Сохранение результатов трассировки в файл (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Сохранение результатов трассировки в таблицу (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [Создание шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)   
 [Создание шаблона на основе выполняемой трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Создать шаблон на основе файла трассировки или таблицы трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Экспорт шаблона трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)   
 [Импорт шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
  
