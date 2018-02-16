---
title: "Заметки о выпуске SQL Server 2014 | Документация Майкрософт"
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4c4922-80b3-4be3-bf71-228247f97004
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4bbb387c935dc07e467125921ef11986ea004c21
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="sql-server-2014-release-notes"></a>SQL Server 2014 Release Notes
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]
В этих примечаниях о версии содержится описание известных проблем, которое необходимо прочитать перед установкой или диагностикой [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="top"></a>Содержание  
[1.0 Перед началом установки](#BeforeInstall)  
  
[2.0 Документация по продукту](#ProdDoc)  
  
[3.0 Ядро СУБД](#DBEngine)  
  
[4.0 Службы Reporting Services](#SSRS)  
  
[5.0 SQL Server 2014 на виртуальных машинах Microsoft Azure](#AzureVM)  
  
[6.0 Службы Analysis Services](#SSAS)  
  
[7.0 Службы Data Quality Services](#DQS)  
  
[8.0 Помощник по обновлению](#UA)  
  
## <a name="BeforeInstall"></a>1.0 Перед началом установки  
  
### <a name="11-limitations-and-restrictions-in-sql-server-2014-rtm"></a>1.1. Ограничения в SQL Server 2014 RTM  
  
#### <a name="111-general-limitations-and-restrictions"></a>1.1.1. Общие ограничения  
  
1.  Обновление с версии SQL Server 2014 CTP 1 до SQL Server 2014 RTM НЕ поддерживается.  
  
2.  Параллельная установка версии SQL Server 2014 CTP 1 с SQL Server 2014 RTM НЕ поддерживается.  
  
3.  Присоединение или восстановление базы данных версии SQL Server 2014 CTP 1 в SQL Server 2014 RTM НЕ поддерживаются.  
  
**Решение.** Отсутствует.  
  
#### <a name="12-considerations-for-upgrading-sql-server-2014-ctp-2-to-sql-server-2014-rtm-and-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2. Соображения по обновлению версии SQL Server 2014 CTP 2 до SQL Server 2014 RTM и переходу с версии SQL Server 2014 RTM на более раннюю версию SQL Server 2014 CTP 2  
  
#### <a name="121-upgrading-from-sql-server-2014-ctp-2-to-sql-server-rtm-is-fully-supported"></a>1.2.1. Обновление с версии SQL Server 2014 CTP 2 до версии SQL Server RTM полностью поддерживается  
В частности, можно:  
  
1.  присоединить базу данных версии SQL Server 2014 CTP 2 к экземпляру SQL Server 2014 RTM;  
  
2.  восстановить резервную копию базы данных, созданную в версии SQL Server 2014 CTP 2, в экземпляре SQL Server 2014 RTM;  
  
3.  обновить до версии SQL Server 2014 RTM на месте;  
  
4.  последовательно обновить до версии SQL Server 2014 RTM; Необходимо переключиться в режим перехода на другой ресурс вручную перед началом последовательного обновления. Подробные сведения см. в статье [Модернизация или обновление серверов группы доступности при минимальных значениях времени простоя и потери данных](http://msdn.microsoft.com/library/dn178483.aspx) .  
  
5.  Данные, собранные наборами элементов сбора данных о производительности транзакций, которые установлены в выпуске SQL Server 2014 CTP 2, нельзя просмотреть с помощью среды SQL Server Management Studio из SQL Server 2014 RTM, и наоборот. Для просмотра данных, собранных набором элементов сбора, который установлен в версии SQL Server 2014 CTP2, используйте среду SQL Server Management Studio из выпуска SQL Server 2014 CTP2, а для просмотра данных, собранных набором элементов сбора, который установлен в SQL Server 2014 RTM, используйте среду SQL Server Management Studio из версии SQL Server 2014 RTM.  
  
### <a name="122-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2.2. Переход с версии SQL Server 2014 RTM на более раннюю версию SQL Server 2014 CTP 2  
Такой режим работы не поддерживается.  
  
**Решений** для перехода на более раннюю версию нет. Перед обновлением до версии SQL Server 2014 RTM рекомендуется создать резервную копию базы данных.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="13-incorrect-version-of-streaminsight-client-on-sql-server-2014-mediaisocab"></a>1.3. Неправильная версия клиента StreamInsight на носителе SQL Server 2014/ISO/CAB  
На носителе SQL Server/ISO/CAB (StreamInsight\\\<архитектура\>\\\<код языка\>) находится неправильная версия StreamInsight.msi и StreamInsightClient.msi.  
  
**Решение.** Скачайте и установите правильную версию со [страницы для скачивания файлов пакета дополнительных компонентов SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
## <a name="ProdDoc"></a>2.0 Документация по продукту  
  
### <a name="21-report-builder-content-is-not-available-in-some-languages"></a>2.1. Содержимое построителя отчетов недоступно на некоторых языках  
**Проблема.** Содержимое построителя отчетов недоступно на следующих языках:  
  
-   греческий (el-GR);  
  
-   норвежский (букмол) (nb-NO);  
  
-   финский (fi-FI);  
  
-   датский (da-DK).  
  
В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]это содержимое находилось в CHM-файле, поставляемом вместе с продуктом, и данные языки поддерживались. CHM-файлы больше не поставляются вместе с продуктом, и содержимое построителя отчетов доступно только в MSDN. MSDN не поддерживает данные языки. Построитель отчетов также удален из TechNet и больше не доступен на этих поддерживаемых языках.  
  
**Решение.** Отсутствует.  
  
### <a name="22-powerpivot-content-is-not-available-in-some-languages"></a>2.2. Содержимое PowerPivot недоступно на некоторых языках  
**Проблема.** Содержимое Power Pivot недоступно на следующих языках:  
  
-   греческий (el-GR);  
  
-   норвежский (букмол) (nb-NO);  
  
-   финский (fi-FI);  
  
-   датский (da-DK).  
  
-   Чешский (cs-CZ)  
  
-   Венгерский (hu-HU)  
  
-   Нидерландский (nl-NL)  
  
-   Польский (pl-PL)  
  
-   Шведский (sv-SE)  
  
-   Турецкий (tr-TR)  
  
-   Португальский (Португалия) (pt-PT)  
  
В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]это содержимое находилось в TechNet и данные языки поддерживались. Это содержимое удалено из TechNet и больше не доступно на этих поддерживаемых языках.  
  
**Решение.** Отсутствует.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="DBEngine"></a>3.0 Ядро СУБД  
  
### <a name="31-changes-made-for-standard-edition-in-sql-server-2014-rtm"></a>3.1. Изменения, внесенные в выпуск Standard в версии SQL Server 2014 RTM  
В версии SQL Server 2014 Standard реализованы следующие изменения:  
  
-   Функция расширения буферного пула допускает максимальный размер, который в четыре раза больше настроенной памяти.  
  
-   Максимальный объем памяти увеличен с 64 до 128 ГБ.  
  
### <a name="32-in-memory-oltp-issues"></a>3.2. Проблемы In-Memory OLTP  
  
#### <a name="321-memory-optimization-advisor-flags-default-constraints-as-incompatible"></a>3.2.1. Помощник по оптимизации памяти помечает ограничения по умолчанию как несовместимые  
**Проблема.** Помощник, оптимизированный для памяти, из среды SQL Server Management Studio помечает все ограничения по умолчанию как несовместимые. Не все ограничения по умолчанию поддерживаются в оптимизированных для памяти таблицах. Помощник не различает поддерживаемые типы ограничений по умолчанию и те из них, которые не поддерживаются. Среди ограничений по умолчанию поддерживаются все ограничения, выражения и встроенные функции, которые поддерживаются в скомпилированных в собственном коде хранимых процедурах. Чтобы просмотреть список функций, поддерживаемых в скомпилированных в собственном коде хранимых процедурах, см. статью [Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде](http://msdn.microsoft.com/library/dn452279(v=sql.120).aspx).  
  
**Решение.** Если с помощью помощника требуется определить причины блокировок, то следует пропускать совместимые ограничения по умолчанию. Чтобы использовать помощник по оптимизации памяти для переноса таблиц, в которых есть совместимые ограничения по умолчанию и нет никаких других причин блокировки, выполните следующие действия.  
  
1.  Удалите ограничения по умолчанию из определения таблицы.  
  
2.  Используйте помощник, чтобы формировать скрипт переноса для таблицы.  
  
3.  Добавьте обратно в скрипт переноса ограничения по умолчанию.  
  
4.  Выполните скрипт переноса.  
  
#### <a name="322-informational-message-file-access-denied-incorrectly-reported-as-an-error-in-the-sql-server-2014-error-log"></a>3.2.2. Информационное сообщение «В доступе к файлу отказано» неверно определяется в журнале ошибок SQL Server 2014 как ошибка  
**Проблема.** При перезапуске сервера, на котором находятся базы данных, содержащие оптимизированные для памяти таблицы, в журнале ошибок SQL Server 2014 могут появиться сообщения об ошибках следующего типа:  
  
```  
[ERROR]Unable to delete file C:\Program Files\Microsoft SQL   
Server\....old.dll. This error may be due to a previous failure to unload   
memory-optimized table DLLs.  
```  
  
Это, по сути, информационное сообщение, никаких действий пользователя при его появлении не требуется.  
  
**Решение.** Отсутствует. Это информационное сообщение.  
  
#### <a name="323-missing-index-details-incorrectly-report-included-columns-for-memory-optimized-table"></a>3.2.3. Сведения об отсутствующих индексах неправильно указывают включенные столбцы для оптимизированной для памяти таблицы  
**Проблема.** Если SQL Server 2014 обнаруживает отсутствующий индекс для запроса к оптимизированной для памяти таблицы, то программа сообщит об отсутствующем индексе в SHOWPLAN_XML, а также в динамических административных представлениях отсутствующих индексов, например sys.dm_db_missing_index_details. В некоторых случаях сведения об отсутствующих индексах будут содержать включенные столбцы. Так как все столбцы неявно включены во все индексы оптимизированных для памяти таблиц, явно указывать включенные столбцы с оптимизированными для памяти индексами нельзя.  
  
**Решение.** Не указывайте предложения INCLUDE с индексами в оптимизированных для памяти таблицах.  
  
#### <a name="324-missing-index-details-omit-missing-indexes-if-a-hash-index-exists-but-is-not-suitable-for-the-query"></a>3.2.4. Сведения об отсутствующих индексах пропускают отсутствующие индексы, если хэш-индекс имеется, но не подходит для запроса  
**Проблема.** Если в запросе есть ссылка на хэш-индекс столбцов оптимизированной для памяти таблицы, но индекс нельзя использовать для запроса, SQL Server 2014 не всегда сообщает об отсутствующем индексе в SHOWPLAN_XML и в динамическом административном представлении sys.dm_db_missing_index_details.  
  
В частности, если запрос содержит предикаты равенства, которые включают подмножество ключевых столбцов индекса, или если он содержит предикаты неравенства, которые включают ключевые столбцы индекса, то индекс HASH нельзя использовать с исходном виде, а для эффективного выполнения запроса потребуется другой индекс.  
  
**Решение.** Если используется хэш-индексы, проверьте запросы и планы запросов, чтобы определить, получат ли запросы преимущество от использования операций Index Seek для подмножеств ключей индекса или операций Index Seek для предикатов неравенства. Если необходимо осуществлять поиск в подмножестве ключа индекса, то используйте либо индекс NONCLUSTERED, либо индекс HASH именно в тех столбцах, в которых требуется выполнять поиск. Если необходимо осуществлять поиск в предикате неравенства, то вместо индекса HASH используйте индекс NONCLUSTERED.  
  
#### <a name="325-failure-when-using-a-memory-optimized-table-and-memory-optimized-table-variable-in-the-same-query-if-the-database-option-readcommittedsnapshot-is-set-to-on"></a>3.2.5. Ошибки при использовании оптимизированной для памяти таблицы и переменной оптимизированной для памяти таблицы в одном запросе, если параметру базы данных READ_COMMITTED_SNAPSHOT задано значение ON  
**Проблема.** Если параметру базы данных READ_COMMITTED_SNAPSHOT задано значение ON и доступ к оптимизированной для памяти таблицы и переменной оптимизированной для памяти таблицы осуществляется в рамках одной инструкции вне контекста пользовательской транзакции, может появиться следующее сообщение об ошибке:  
  
```  
Msg 41359  
A query that accesses memory optimized tables using the READ COMMITTED  
isolation level, cannot access disk based tables when the database option  
READ_COMMITTED_SNAPSHOT is set to ON. Provide a supported isolation level  
for the memory optimized table using a table hint, such as WITH (SNAPSHOT).  
```  
  
**Решение.** Используйте табличное указание WITH (SNAPSHOT) с табличной переменной или установите для параметра базы данных MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT значение ON с помощью следующей инструкции:  
  
```  
ALTER DATABASE CURRENT   
SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
```  
  
#### <a name="326-procedure-and-query-execution-statistics-for-natively-compiled-stored-procedures-record-worker-time-in-multiples-of-1000"></a>3.2.6. Статистика выполнения процедур и запросов для скомпилированных в собственном коде хранимых процедур формирует запись времени рабочего потока, кратное 1000  
**Проблема.** После включения сбора статистики выполнения процедур или запросов для скомпилированных в собственном коде хранимых процедур с помощью sp_xtp_control_proc_exec_stats или sp_xtp_control_query_exec_stats в динамических административных представлениях sys.dm_exec_procedure_stats и sys.dm_exec_query_stats появится значение *_worker_time, кратное 1000. Выполнения запросов, время рабочей роли которых меньше 500 микросекунд будет отображаться как значение worker_time, равное 0.  
  
**Решение.** Отсутствует. Не следует считать верным значение worker_time, указанное в динамических административных представлениях статистики выполнения для краткосрочных запросов из скомпилированных в собственном коде хранимых процедур.  
  
#### <a name="327-error-with-showplanxml-for-natively-compiled-stored-procedures-that-contain-long-expressions"></a>3.2.7. Ошибка с SHOWPLAN_XML для скомпилированных в собственном коде хранимых процедур, которые содержат длинные выражения  
**Проблема.** Если скомпилированная в собственном коде хранимая процедура содержит длинное выражение, получающее SHOWPLAN_XML для процедуры либо с помощью параметра T-SQL SHOWPLAN_XML ON, либо с помощью параметра "Показать предполагаемый план выполнения" в Management Studio, то это может привести к возникновению следующей ошибки:  
  
```  
Msg 41322. MAT/PIT export/import encountered a failure for memory  
optimized table or natively compiled stored procedure with object ID  
278292051 in database ID 6. The error code was  
0xc00cee81.  
```  
  
**Решение.** Есть два решения:  
  
1.  Заключить выражение в скобки, как в приведенном далее примере:  
  
    Вместо:  
  
    ```  
    SELECT @v0 + @v1 + @v2 + ... + @v199  
    ```  
  
    Записать:  
  
    ```  
    SELECT((@v0 + ... + @v49) + (@v50 + ... + @v99)) + ((@v100 + ... + @v149) + (@v150 + ... + @v199))  
    ```  
  
2.  Создайте вторую процедуру с немного упрощенным выражением для showplan — в общих чертах план должен быть таким же. Например, вместо:  
  
    ```  
    SELECT @v0 +@v1 +@v2 +...+@v199  
    ```  
  
    Записать:  
  
    ```  
    SELECT @v0 +@v1  
    ```  
  
#### <a name="328-using-a-string-parameter-or-variable-with-datepart-and-related-functions-in-a-natively-compiled-stored-procedure-results-in-an-error"></a>3.2.8. Использование строкового параметра или переменной с DATEPART и связанными функциями в скомпилированной в собственном коде хранимой процедуре приводит к ошибке  
**Проблема.** При использовании параметра или переменной, которая имеет строковый тип данных, например (var)char или n(var)char со встроенными функциями DATEPART, DAY, MONTH и YEAR, внутри скомпилированной в собственном коде хранимой процедуры отображается сообщение об ошибке, указывающее, что тип данных datetimeoffset не поддерживается скомпилированными в собственном коде хранимыми процедурами.  
  
**Решение.** Присвойте строковый параметр или переменную новой переменной типа datetime2 и передайте эту переменную в функцию DATEPART, DAY, MONTH или YEAR. Пример:  
  
```  
DECLARE @d datetime2 = @string  
DATEPART(weekday, @d)  
```  
  
#### <a name="329-native-compilation-advisor-flags-delete-from-clauses-incorrectly"></a>3.2.9. Помощник по собственной компиляции неправильно помечает предложения DELETE FROM  
**Проблема.** Помощник по компиляции в собственный код неправильно помечает предложения FROM DELETE внутри хранимой процедуры как несовместимые.  
  
**Решение.** Отсутствует.  
  
### <a name="33-register-through-ssms-adds-dac-meta-data-with-mismatched-instance-ids"></a>3.3. При регистрации через среду SSMS добавляются метаданные приложения уровня данных с несовпадающими идентификаторами экземпляра  
**Проблема.** При регистрации или удалении пакета приложения уровня данных (DACPAC) с помощью среды SQL Server Management Studio таблицы SYSDAC* не обновляются правильно, чтобы позволить пользователю выполнять запросы к журналу DACPAC базы данных.  Instance_id для sysdac_history_internal и sysdac_instances_internal не совпадают, из-за чего соединение невозможно.  
  
**Решение.** Эта проблема исправлена в платформе [Data-Tier Application Framework](https://www.microsoft.com/download/details.aspx?id=42295), которая распространяется в составе пакета дополнительных компонентов.  После применения обновления все новые записи журнала будут использовать значение, указанное для instance_id в таблице sysdac_instances_internal.  
  
Если уже имеется проблема с несовпадающими значениями instance_id, единственным способом устранить их является подключиться к серверу от имени пользователя с правами на запись в базу данных MSDB и исправить значения instance_id на верные.  Если есть несколько событий регистрации и отмены регистрации для одной и той же базы данных, необходимо изучить значения даты и времени, чтобы определить, какие записи соответствуют текущим значениям instance_id.  
  
1.  Подключитесь к серверу в среде SQL Server Management Studio с помощью имени входа, которое имеет разрешения на обновление в MSDB.  
  
2.  Открытие нового запроса в базе данных MSDB.  
  
3.  Выполните этот запрос для просмотра всех активных экземпляров приложения уровня данных.  Найдите экземпляр, который требуется исправить, и запишите значение instance_id:  
  
    `select * from` sysdac_instances_internal  
  
4.  Выполните этот запрос, чтобы отобразить все записи журнала.  
  
    `select * from` sysdac_history_internal  
  
5.  Определите строки, которые должны соответствовать исправляемому экземпляру  
  
6.  Обновите значение sysdac_history_internal.instance_id, задав значение, которое вы записали на шаге 3 (из таблицы sysdac_instances_internal):  
  
    `update` sysdac_history_internal `set` instance_id = '\<значение с шага 3\>' `where` \<выражение, соответствующее строкам, которые нужно обновить\>  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="SSRS"></a>4.0 Службы Reporting Services  
  
### <a name="41-the-sql-server-2012-reporting-services-native-mode-report-server-cannot-run-side-by-side-with-sql-server-2014-reporting-services-sharepoint-components"></a>4.1. Сервер отчетов служб SQL Server 2012 Reporting Services в собственном режиме не может работать параллельно с компонентами SharePoint служб SQL Server 2014 Reporting Services  
**Проблема.** Служба Windows [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , выполняющаяся в основном режиме, SQL Server Reporting Services (ReportingServicesService.exe), не запускается, если на компьютере установлены компоненты SharePoint служб [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
**Решение.** Удалите компоненты SharePoint служб [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и перезапустите службу Windows Microsoft SQL Server 2012 Reporting Services.  
  
**Дополнительные сведения:**  
  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Службы в основном режиме не могут работать параллельно со следующими компонентами:  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint Shared Service.  
  
При параллельной установке служба Windows для служб [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], работающих в основном режиме, не запускается. В журнал событий Windows будут помещены примерно следующие сообщения:  
  
```  
Log Name:   Application  
Source:          Report Server (<SQL instance ID>)  
Event ID:        117  
Task Category:   Startup/Shutdown  
Level:           Error  
Keywords:        Classic  
Description:     The report server database is an invalid version.  
  
Log Name:      Application  
Source:        Report Server (<SQL instance ID>)  
Event ID:      107  
Task Category: Management  
Level:         Error  
Keywords:      Classic  
Description:   Report Server (DENALI) cannot connect to the report server database.  
```  
  
Дополнительные сведения см. в разделе [Рекомендации, советы и сведения по устранению неполадок со службами SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
### <a name="42-required-upgrade-order-for-multi-node-sharepoint-farm-to-sql-server-2014-reporting-services"></a>4.2. Требуемый порядок обновления для фермы SharePoint с несколькими узлами до служб SQL Server 2014 Reporting Services  
**Проблема.** Преобразование отчета для просмотра в ферме с несколькими узлами завершается ошибкой, если экземпляры общей службы SharePoint служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обновляются до всех экземпляров надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint.  
  
**Решение.** В ферме SharePoint с несколькими узлами:  
  
1.  Сначала обновите все экземпляры надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint.  
  
2.  Затем обновите все экземпляры общей службы SharePoint служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
Дополнительные сведения см. в разделе [Рекомендации, советы и сведения по устранению неполадок со службами SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="AzureVM"></a>5.0 SQL Server 2014 RTM на виртуальных машинах Microsoft Azure  
  
### <a name="51-the-add-azure-replica-wizard-returns-an-error-when-configuring-an-availability-group-listener-in-windows-azure"></a>5.1. Мастер добавления реплики Azure возвращает ошибку при настройке прослушивателя группы доступности в Windows Azure  
**Проблема.** Если в группе доступности имеется прослушиватель, мастер добавления реплики Azure возвращает ошибку при попытке настроить прослушиватель в Microsoft Azure.  
  
Это происходит потому, что прослушиватели групп доступности требуют назначения одного IP-адреса для каждой подсети, в которой размещены реплики группы доступности, включая подсеть Azure.  
  
**Решение:**  
  
1.  На странице прослушивателя назначьте свободный статический IP-адрес из подсети Azure, в которой будет размещаться реплика группы доступности, прослушивателю группы доступности.  
  
    Это позволит мастеру завершить добавление реплики в Windows Azure.  
  
2.  Когда мастер завершит работу, необходимо будет закончить настройку прослушивателя в Windows Azure, как описано в разделе [Настройка прослушивателя для групп доступности AlwaysOn в Windows Azure](http://msdn.microsoft.com/library/dn376546.aspx)  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="SSAS"></a>6.0 Службы Analysis Services  
  
### <a name="61-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2010-new-farm-configured-with-sql-server-2014"></a>6.1. MSOLAP.5 необходимо скачать, установить и зарегистрировать для новой фермы SharePoint 2010, настроенной с SQL Server 2014  
**Проблема:**  
  
-   В ферме SharePoint 2010, настроенной с развертыванием SQL Server 2014 RTM, книги PowerPivot не могут подключаться к моделям данных, так как не установлен поставщик, указанный в строке подключения.  
  
**Решение:**  
  
1.  Загрузите поставщик MSOLAP.5 из пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Установите поставщик на серверах приложений, на которых запущены службы Excel. Дополнительные сведения см. в подразделе «Microsoft Analysis Services OLE DB Provider для Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)» [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Зарегистрируйте MSOLAP.5 в качестве надежного поставщика в службах Excel SharePoint. Дополнительные сведения см. в разделе [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Дополнительные сведения:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит MSOLAP.6. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssGemini](../includes/ssgemini-md.md)] используют MSOLAP.5. Если MSOLAP.5 не установлен на компьютере, где работают службы Excel, то службы Excel не могут загружать модели данных.  
  
### <a name="62-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2013-new-farm-configured-with-sql-server-2014"></a>6.2. MSOLAP.5 необходимо загрузить, установить и зарегистрировать для новой фермы SharePoint 2013, настроенной с SQL Server 2014  
**Проблема:**  
  
-   В ферме SharePoint 2013, настроенной с развертыванием [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , книги Excel, обращающиеся к поставщику MSOLAP.5, не могут подключаться к моделям данных, так как не установлен поставщик, указанный в строке подключения.  
  
**Решение:**  
  
1.  Загрузите поставщик MSOLAP.5 из пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Установите поставщик на серверах приложений, на которых запущены службы Excel. Дополнительные сведения см. в подразделе «Microsoft Analysis Services OLE DB Provider для Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)» [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Зарегистрируйте MSOLAP.5 в качестве надежного поставщика в службах Excel SharePoint. Дополнительные сведения см. в разделе [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Дополнительные сведения:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит MSOLAP.6. но книги PowerPivot SQL Server 2014 используют MSOLAP.5. Если MSOLAP.5 не установлен на компьютере, где работают службы Excel, то службы Excel не могут загружать модели данных.  
  
### <a name="63-corrupt-data-refresh-schedules"></a>6.3. Повреждение расписаний обновления данных  
**Проблема:**  
  
-   Изменяется расписание обновления, и расписание становится поврежденным и недоступным.  
  
**Решение:**  
  
1.  В Microsoft Excel очистите пользовательские дополнительные свойства. Дополнительные сведения см. в разделе «Решение» следующей статьи базы знаний [KB 2927748 КБ](http://support.microsoft.com/kb/2927748).  
  
**Дополнительные сведения:**  
  
-   При изменении расписания обновления данных в книге, если сериализованная длина расписания меньше, чем исходное расписание, размер буфера неправильно обновляется и новые сведения о расписании объединяются со сведениями старого расписания, в результате чего оно становится поврежденными.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="DQS"></a>7.0 Службы Data Quality Services  
  
### <a name="71-no-cross-version-support-for-data-quality-services-in-master-data-services"></a>7.1. Отсутствие перекрестной поддержки версий для служб Data Quality Services в службах Master Data Services  
**Проблема.** Не поддерживаются следующие сценарии:  
  
-   Службы Master Data Services 2014, размещенные в базе данных компонента SQL Server Database Engine в SQL Server 2012 с установленными службами Data Quality Services 2012.  
  
-   Службы Master Data Services 2012, размещенные в базе данных ядра СУБД SQL Server в SQL Server 2014 с установленными службами Data Quality Services 2014.  
  
**Решение.** Используйте такую же версию служб Master Data Services, как и у базы данных ядра СУБД и служб Data Quality Services.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
## <a name="UA"></a>8.0 Проблемы с советником по переходу  
  
### <a name="81--sql-server-2014-upgrade-advisor-reports-irrelevant-upgrade-issues-for-sql-server-reporting-services"></a>8.1. Помощник по обновлению SQL Server 2014 сообщает о несуществующих проблемах с обновлением для служб SQL Server Reporting Services  
**Проблема.** Помощник по обновлению SQL Server (SSUA), поставляемый с носителем SQL Server 2014, неверно сообщает о разных ошибках при анализе сервера SQL Server Reporting Services.  
  
**Решение.** Эта проблема исправлена в помощнике по обновлению SQL Server из [пакета дополнительных компонентов SQL Server 2014 для SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
### <a name="82--sql-server-2014-upgrade-advisor-reports-an-error-when-analyzing-sql-server-integration-services-server"></a>8.2. Помощник по обновлению SQL Server 2014 сообщает об ошибке при анализе сервера служб SQL Server Integration Services  
**Проблема.** Помощник по обновлению SQL Server (SSUA), поставляемый с носителем SQL Server 2014, сообщает об ошибке при анализе сервера SQL Server Integration Services.  Сообщение, отображаемое пользователю:  
  
```  
The installed version of Integration Services does not support Upgrade Advisor.   
The assembly information is "Microsoft.SqlServer.ManagedDTS, Version=11.0.0.0,   
Culture=neutral, PublicKeyToken=89845dcd8080cc91  
```  
  
**Решение.** Эта проблема исправлена в помощнике по обновлению SQL Server из [пакета дополнительных компонентов SQL Server 2014 для SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
![Значок стрелки, используемый для ссылки возврата в начало](../sql-server/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[В начало](#top)  
  
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
