---
title: sys.database_connection_stats (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 03/25/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_connection_stats
- database_connection_stats
- database_connection_stats_TSQL
- sys.database_connection_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_connection_stats
- database_connection_stats
ms.assetid: 5c8cece0-63b0-4dee-8db7-6b43d94027ec
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 0ab4255a4c13199a445335eef491ca0986ab3287
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabaseconnectionstats-azure-sql-database"></a>sys.database_connection_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Содержит статистику для [!INCLUDE[ssSDS](../../includes/sssds-md.md)] базы данных **подключения** события, предоставляя общие сведения о базе данных успешных и неудачных подключений. Дополнительные сведения о событиях подключения см. в разделе типы событий в [sys.event_log &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
|Статистика|Тип|Описание|  
|---------------|----------|-----------------|  
|**database_name**|**sysname**|Имя базы данных.|  
|**start_time**|**datetime2**|Дата и время начала интервала статистической обработки в формате UTC. Время всегда кратно 5 минутам. Например:<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|Дата и время окончания интервала статистической обработки в формате UTC. **End_time** — всегда на пять минут больше соответствующего **start_time** в той же строке.|  
|**success_count**|**int**|Число успешных соединений.|  
|**total_failure_count**|**int**|Общее число неудачных попыток соединения. Это сумма **connection_failure_count**, **terminated_connection_count**, и **throttled_connection_count**и не включает события взаимоблокировки.|  
|**connection_failure_count**|**int**|Количество сбоев входа.|  
|**terminated_connection_count**|**int**|***Применимо только для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11.***<br /><br /> Число прерванных соединений.|  
|**throttled_connection_count**|**int**|***Применимо только для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11.***<br /><br /> Число регулируемых соединений.|  
  
## <a name="remarks"></a>Замечания  
  
### <a name="event-aggregation"></a>Статистическая обработка событий  
 Сведения о событиях для этого представления собираются и обрабатываются каждые 5 минут. Столбцы счетчиков представляют количество возникновения определенного события подключения для конкретной базы данных в течение заданного интервала времени.  
  
 Например, если пользователю не удается подключиться к базе данных Database1 семь раз с 11:00 до 11:05 5 февраля 2012 г. (UTC), то эти сведения доступны в одной строке в следующем виде:  
  
|**database_name**|**start_time**|**end_time**|**success_count**|**total_failure_count**|**connection_failure_count**|**terminated_connection_count**|**throttled_connection_count**|  
|------------------------|---------------------|-------------------|------------------------|-------------------------------|------------------------------------|---------------------------------------|--------------------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`0`|`7`|`7`|`0`|`0`|  
  
### <a name="interval-starttime-and-endtime"></a>start_time и end_time интервала  
 Событие включается в интервал статистической обработки при возникновении события *на* или *после *** start_time** и *перед *** end_time** для этого интервала. Например, событие, которое происходит точно в `2012-10-30 19:25:00.0000000`, будет включено только во второй интервал, показанный ниже.  
  
```  
  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>Обновление данных  
 Данные в этом представлении с течением времени накапливаются. Как правило, данные накапливаются в течение часа с начала интервала статистической обработки, но для отображения всех данных в представлении может потребоваться до 24 часов. В течение этого времени сведения в одной строке могут периодически обновляться.  
  
### <a name="data-retention"></a>Хранение данных  
 Данные в этом представлении сохраняются не более 30 дней или по возможности меньше в зависимости от числа баз данных на логическом сервере и числа уникальных событий, создаваемых каждой базой данных. Для сохранения этих данных в течение более длительного периода скопируйте их в отдельную базу данных. После создания первоначальной копии представления строки могут быть обновлены по мере накопления данных. Чтобы копия данных была актуальной, периодически выполняйте просмотр таблицы для определения увеличения числа событий существующих строк и для определения новых строк (вы можете определить уникальные строки с помощью времени начала и окончания интервала), а затем обновить свою копию данных с применением этих изменений.  
  
### <a name="errors-not-included"></a>Исключенные ошибки  
 Это представление может содержать не все сведения о подключениях и ошибках:  
  
-   Это представление содержит не все [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ошибки, которые могут возникнуть только указанные в типы событий в базы данных [sys.event_log &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
-   Если в центре обработки данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] возникла ошибка компьютера, в таблице событий может отсутствовать небольшой объем данных логического сервера.  
  
-   Если IP-адрес заблокирован через DoSGuard, события подключения с этого IP-адреса не могут собираться и не будут отображаться в этом представлении.  
  
## <a name="permissions"></a>Разрешения  
 Пользователи, имеющие разрешение на доступ к **master** базы данных имеют доступ только для чтения к этому представлению.  
  
## <a name="example"></a>Пример  
 В следующем примере показано запрос **sys.database_connection_stats** для возвращает сводку подключений к базе данных, происходившим с полудня 25 сентября до полудня/28/2011 г. (UTC). По умолчанию результаты запроса сортируются по **start_time** (по возрастанию).  
  
```  
SELECT *  
FROM sys.database_connection_stats   
WHERE start_time>='2011-09-25:12:00:00' and end_time<='2011-09-28 12:00:00';  
```  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок базы данных Azure SQL для Windows](http://msdn.microsoft.com/library/windowsazure/ee730906.aspx)  
  
  
