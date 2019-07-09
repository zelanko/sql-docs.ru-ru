---
title: Устранение проблем с нехваткой памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e31f36624e8923722612810836df5d2a57b6b686
ms.sourcegitcommit: 9af07bd57b76a34d3447e9e15f8bd3b17709140a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624411"
---
# <a name="resolve-out-of-memory-issues"></a>Устранение проблем нехватки памяти
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] использует больше памяти, чем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и делает это по-другому. Возможно, что объем памяти, установленный и выделенный для [!INCLUDE[hek_2](../../includes/hek-2-md.md)] , станет недостаточным для растущих потребностей. В таком случае может возникнуть нехватка памяти. В этом разделе описывается восстановление из ситуации с нехваткой памяти. В статье [Наблюдение и устранение неисправностей при использовании памяти](monitor-and-troubleshoot-memory-usage.md) вы найдете рекомендации, которые помогут вам избежать многих ситуаций нехватки памяти.  
  
## <a name="covered-in-this-topic"></a>Темы данного раздела  
  
|Раздел|Обзор|  
|-----------|--------------|  
| [устранить ошибки восстановления базы данных, возникающие из-за нехватки памяти](#resolve-database-restore-failures-due-to-oom) |Что делать, если вы получите сообщение об ошибке "Выполнение операции восстановления для базы данных *\<имя_базы_данных>* завершилось неудачей из-за нехватки памяти в пуле ресурсов *\<имя_пула_ресурсов>* ".|  
| [устранить влияния нехватки свободной памяти на рабочую нагрузку](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|Что следует предпринять, если обнаружится, что недостаток памяти отрицательно влияет на производительность.|  
| [Устранение ошибок выделения страниц, возникших из-за нехватки памяти при наличии достаточных ресурсов памяти](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |Что делать, если вы получите сообщение об ошибке "Производится отключение выделения страниц для базы данных *\<имя_базы_данных>* из-за нехватки памяти в пуле ресурсов *\<имя_пула_ресурсов>* ", если объема доступной памяти достаточно для выполнения операции.|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a>устранить ошибки восстановления базы данных, возникающие из-за нехватки памяти  
 При попытке восстановить базу данных может появиться сообщение об ошибке: «Операция восстановления завершилась сбоем для базы данных " *\<databaseName >* «из-за нехватки памяти в пуле ресурсов» *\<resourcePoolName >* ".» Прежде чем можно будет восстановить базу данных, необходимо устранить проблемы нехватки памяти, увеличив объем доступной памяти.  
  
 Чтобы устранить ошибку восстановления из-за OOM, нужно увеличить объем доступной памяти с помощью любого из следующих средств, чтобы временно увеличить объем памяти, доступной для операции восстановления.  
  
-   Временно закройте выполняющиеся приложения.   
    Закрыв одно или несколько выполняющихся приложений, например Visual Studio, Internet Explorer, OneNote и другие программы, можно освободить используемую ими память для операции восстановления. Эти приложения можно будет перезапустить после успешного завершения восстановления.  
  
-   Увеличьте значение MAX_MEMORY_PERCENT.   
    В этом фрагменте кода значение параметра MAX_MEMORY_PERCENT для пула ресурсов PoolHk увеличивается до 70 % от установленной памяти.  
  
    > [!IMPORTANT]  
    >  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
    > См. в разделе [рекомендации: Использование In-Memory OLTP в среде ВМ](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) Дополнительные сведения.  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     Сведения о максимальных значениях для MAX_MEMORY_PERCENT см. в разделе [процент доступной памяти для оптимизированных для памяти таблиц и индексов](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)
  
-   Измените значение **max server memory**.  
    Дополнительные сведения о настройке **максимальной памяти сервера** см. в разделе [Оптимизация производительности сервера с помощью параметров конфигурации памяти](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a>устранить влияния нехватки свободной памяти на рабочую нагрузку  
 Очевидно, проще всего вообще избегать ситуаций, связанных с нехваткой памяти. Помочь в этом может хорошее планирование и отслеживание. Однако даже самое хорошее планирование не гарантирует стабильной работы, и возникновение нехватки памяти всегда возможно. Для устранения этой ситуации необходимо выполнить два действия.  
  
1.  [Откройте выделенное административное соединение](#open-a-dac-dedicated-administrator-connection) 
  
2.  [Примените действие по исправлению](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a>Откройте выделенное административное соединение  
 В Microsoft SQL Server есть выделенное административное соединение. С помощью выделенного административного соединения администратор может обращаться к запущенному экземпляру ядра СУБД SQL Server для устранения неполадок на сервере, даже если сервер не отвечает на другие клиентские соединения. Выделенные административные соединения доступны в программе `sqlcmd` и в среде SQL Server Management Studio (SSMS).  
  
 Рекомендации по использованию `sqlcmd` и выделенных административных соединений см. в разделе [Использование выделенного административного соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md). Рекомендации по использованию DAC в SSMS см. в разделе [как: Использование выделенного административного соединения с SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).  
  
### <a name="take-corrective-action"></a>Примените действие по исправлению  
 Для устранения проблемы с нехваткой памяти необходимо либо освободить имеющуюся память путем сокращения объема ее использования, либо выделить дополнительный объем памяти таблицам в памяти.  
  
#### <a name="free-up-existing-memory"></a>Освобождение имеющейся памяти  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Удаление неважных строк оптимизированных для памяти таблиц и ожидание выполнения сборки мусора  
 Можно удалить неважные строки из оптимизированной для памяти таблицы. Сборщик мусора делает объем памяти, используемый этими строками, доступным. . Компонент In-memory OLTP выполняет сбор ненужных строк агрессивно. Однако долго выполняющаяся транзакция может помешать сбору мусора. Например, если имеется транзакция, которая выполняется в течение 5 минут, все версии строк, созданные из-за операций обновления или удаления во время выполнения транзакции, не подпадают под сборку мусора.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Переместить одну или несколько строк в таблице на диске  
 В следующих статьях TechNet представлены рекомендации по перемещению строк из таблиц, оптимизированных для памяти, в таблицы на диске.  
  
-   [Секционирование уровня приложения](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Модель приложения для секционирования таблиц, оптимизированных для памяти](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Увеличение объема доступной памяти  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>Увеличение значения MAX_MEMORY_PERCENT для пула ресурсов  
 Если именованный пул ресурсов для таблиц в памяти еще не создан, то его необходимо создать и привязать к нему базы данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] . Инструкции по созданию пула ресурсов и привязки к нему баз данных [см. в разделе](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
 Если база данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] привязана к пулу ресурсов, то пользователь может увеличить процент памяти, доступной для пула. Инструкции по изменению значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для пула ресурсов см. в подразделе [Изменение параметров MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) .  
  
 Увеличьте значение MAX_MEMORY_PERCENT.   
В этом фрагменте кода значение параметра MAX_MEMORY_PERCENT для пула ресурсов PoolHk увеличивается до 70 % от установленной памяти.  
  
> [!IMPORTANT]  
>  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
> См. в разделе [рекомендации: Использование In-Memory OLTP в среде ВМ](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) Дополнительные сведения.  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 Дополнительные сведения о максимальных значениях параметра MAX_MEMORY_PERCENT см в разделе [Процент памяти, доступной для оптимизированных для памяти таблиц и индексов](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).  
  
##### <a name="install-additional-memory"></a>Установка дополнительной памяти  
 В конечном счете наилучшим решением является установка дополнительной памяти. Если выбран этот вариант, то необходимо учитывать, что, скорее всего, также можно будет увеличить значение MAX_MEMORY_PERCENT (см. подраздел [Изменение параметров MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)), так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вряд ли будет нужно больше памяти, а это позволит выделить большую часть или даже всю установленную новую память пулу ресурсов.  
  
> [!IMPORTANT]  
>  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
> См. в разделе [рекомендации: Использование In-Memory OLTP в среде ВМ](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) Дополнительные сведения.  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a>Устранение ошибок выделения страниц, возникших из-за нехватки памяти при наличии достаточных ресурсов памяти  
 Если вы получаете сообщение об ошибке «запрет распределения страниц для базы данных " *\<databaseName >* «из-за нехватки памяти в пуле ресурсов» *\<resourcePoolName >* '. См. в разделе "<https://go.microsoft.com/fwlink/?LinkId=330673>" Дополнительные сведения.» а доступной физической памяти достаточно для выделения страницы, это может быть связано с отключенным регулятором ресурсов. Если регулятор ресурсов отключен, то MEMORYBROKER_FOR_RESERVE вызывает искусственную нагрузку на ресурсы памяти.  
  
 Для устранения этой ошибки необходимо включить регулятор ресурсов.  
  
 См. в разделе [Включение регулятора ресурсов](https://technet.microsoft.com/library/bb895149.aspx) дополнительные сведения об ограничениях, а также рекомендации по включению регулятора ресурсов через обозреватель объектов, свойства регулятора ресурсов или Transact-SQL.  
  
## <a name="see-also"></a>См. также  
 [Управление памятью для компонента In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md)   
 [Наблюдение и устранение неисправностей при использовании памяти](monitor-and-troubleshoot-memory-usage.md)   
 [Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Советы и рекомендации: Использование In-Memory OLTP в среде ВМ](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
