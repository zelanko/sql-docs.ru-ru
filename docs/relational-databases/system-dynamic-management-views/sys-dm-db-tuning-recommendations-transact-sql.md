---
title: sys.dm_db_tuning_recommendations (Transact-SQL) | Документация Майкрософт
description: Узнайте, как обнаружить потенциальные проблемы производительности и рекомендованные способы устранения проблемы в SQL Server и базы данных SQL Azure
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_tuning_recommendations
- dm_db_tuning_recommendations
- sys.dm_db_tuning_recommendations_TSQL
- dm_db_tuning_recommendations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database tuning recommendations feature [SQL Server], sys.dm_db_tuning_recommendations dynamic management view
- sys.dm_db_tuning_recommendations dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 21756cadbfb924e95edd261942f018fb6aef6a4c
ms.sourcegitcommit: 170c275ece5969ff0c8c413987c4f2062459db21
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54226521"
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>sys.DM\_db\_настройке\_рекомендации (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Возвращает подробные сведения о рекомендации по настройке.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать раскрытия этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.

| **Имя столбца** | **Data type** | **Описание** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Уникальное имя рекомендации. |
| **type** | **nvarchar(4000)** | Параметр автоматической настройки, которая является создателем рекомендаций, например, имя `FORCE_LAST_GOOD_PLAN` |
| **Причина** | **nvarchar(4000)** | Причина, почему эта рекомендация была предоставлена. |
| **Допустимые\_с момента** | **datetime2** | В первый раз, эта рекомендация была создана. |
| **последний\_обновления** | **datetime2** | Время последнего создания этой рекомендации. |
| **state** | **nvarchar(4000)** | Документ JSON, описывающий состояние рекомендации. Доступны следующие поля:<br />-   `currentValue` — Текущее состояние рекомендации.<br />-   `reason` -Константа, которая описывает, почему мы рекомендуем в текущем состоянии.|
| **—\_исполняемый\_действие** | **bit** | 1 = рекомендации, которые могут быть выполнены в базе данных с помощью [!INCLUDE[tsql_md](../../includes/tsql-md.md)] скрипта.<br />0 = рекомендация не может быть выполнена в базе данных (например: сведения о рекомендации только из цифр или возвращенного в предыдущее состояние) |
| **—\_revertable\_действия** | **bit** | 1 = рекомендации можно автоматически отслеживаться и вернуть компонентом Database engine.<br />0 = рекомендация не может быть автоматически отслеживаться и отменены. Большинство &quot;исполняемый&quot; действий &quot;revertable&quot;. |
| **выполнение\_действие\_запустить\_времени** | **datetime2** | Дата применения рекомендации. |
| **выполнение\_действие\_длительность** | **time** | Длительность выполнения действия. |
| **выполнение\_действие\_инициированный\_по** | **nvarchar(4000)** | `User` = Пользователь вручную принудительно плана в рекомендацию. <br /> `System` = Система автоматически применяется рекомендация. |
| **выполнение\_действие\_инициированный\_времени** | **datetime2** | Дата рекомендация была применена. |
| **Отменить\_действие\_запустить\_времени** | **datetime2** | Дата рекомендация была отменена. |
| **Отменить\_действие\_длительность** | **time** | Длительность действия отмены изменений. |
| **Отменить\_действие\_инициированный\_по** | **nvarchar(4000)** | `User` = Пользователь вручную ухудшением Рекомендуемый план. <br /> `System` = Система автоматически возвращается рекомендации. |
| **Отменить\_действие\_инициированный\_времени** | **datetime2** | Дата рекомендация была отменена. |
| **Оценка** | **int** | Предполагаемое значение/влияние этой рекомендации по 0 – 100 масштабирования (чем больше чем) |
| **Сведения о** | **nvarchar(max)** | Документ JSON, который содержит дополнительные сведения об этой рекомендации. Доступны следующие поля:<br /><br />`planForceDetails`<br />-    `queryId` -запрос\_идентификатор регрессионных запроса.<br />-    `regressedPlanId` -plan_id из плана с ухудшением.<br />-   `regressedPlanExecutionCount` -Обнаруживается число выполнений запроса с помощью плана с ухудшением перед регрессии.<br />-    `regressedPlanAbortedCount` -Количество обнаруженных ошибок во время выполнения плана с ухудшением.<br />-    `regressedPlanCpuTimeAverage` -Среднее время ЦП, затраченное на выполнение регрессионных запроса до обнаружения регрессии.<br />-    `regressedPlanCpuTimeStddev` — Обнаружена стандартное отклонение времени ЦП, затраченное на выполнение запроса регрессионных перед регрессии.<br />-    `recommendedPlanId` -plan_id плана, который должен быть принудительно.<br />-   `recommendedPlanExecutionCount`— Количество выполнений запроса с планом, следует принудительно до обнаружения регрессии.<br />-    `recommendedPlanAbortedCount` — Количество обнаруженные ошибки во время выполнения плана, на который должен быть принудительно.<br />-    `recommendedPlanCpuTimeAverage` -Среднее время ЦП, затраченное на выполнение запроса с план, который должен быть принудительно (вычисляется до обнаружения регрессии).<br />-    `recommendedPlanCpuTimeStddev` Стандартное отклонение времени ЦП, затраченное на выполнение запроса регрессионных перед регрессии обнаруживается.<br /><br />`implementationDetails`<br />-  `method` Метод, который следует использовать для исправления регрессии. Значение всегда равно `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)] скрипт, который должен быть выполнен для принудительного Рекомендуемый план. |
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые функцией `sys.dm_db_tuning_recommendations` обновляется, когда компонент database engine определяет потенциальные снижением производительности запросов и не сохраняется. Рекомендации хранится только до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускается. Если необходимо сохранить их после перезагрузки сервера, администраторы баз данных должны периодически делать резервные копии рекомендации по настройке. 

 `currentValue` в поле `state` столбец может иметь следующие значения:
 
 | Состояние | Описание |
 |--------|-------------|
 | `Active` | Мы рекомендуем активных и еще не примененные. Пользователь может выполнить скрипт рекомендаций и выполнить его вручную. |
 | `Verifying` | Применение рекомендации по [!INCLUDE[ssde_md](../../includes/ssde_md.md)] и процесс внутренней проверки сравнивает принудительного плана с помощью плана с ухудшением производительности. |
 | `Success` | Рекомендация успешно применена. |
 | `Reverted` | Так как существуют не значительный прирост производительности, будет выполнен откат рекомендации. |
 | `Expired` | Рекомендация истек и не может использоваться больше. |

Документ JSON в `state` столбец содержит причину, которая описывает, почему является рекомендацией в текущем состоянии. Может принимать следующие значения в поле Причина: 

| Причина | Описание |
|--------|-------------|
| `SchemaChanged` | Истек срок действия рекомендацию, из-за изменения схемы таблицы, на которую указывает ссылка. |
| `StatisticsChanged`| Рекомендация истекло из-за изменения статистики по указанной таблице. |
| `ForcingFailed` | Рекомендуемый план нельзя принудительно применить к запросу. Найти `last_force_failure_reason` в [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) представление, чтобы найти причину сбоя. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` параметр будет отключен пользователем во время процесса проверки. Включить `FORCE_LAST_GOOD_PLAN` использование параметра [ALTER DATABASE ЗАДАТЬ AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) инструкции или принудительного плана, вручную с помощью скрипта в `[details]` столбца. |
| `UnsupportedStatementType` | План нельзя принудительно применить к запросу. Примеры неподдерживаемых запросов являются курсоры и `INSERT BULK` инструкции. |
| `LastGoodPlanForced` | Рекомендация успешно применена. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] идентифицировать потенциальные снижение производительности, но `FORCE_LAST_GOOD_PLAN` параметр не включен, — см. в разделе [ALTER DATABASE ЗАДАТЬ AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Применить рекомендацию вручную или включить `FORCE_LAST_GOOD_PLAN` параметр. |
| `VerificationAborted`| Процесс проверки прервана из-за перезапуска или Store запроса очистки. |
| `VerificationForcedQueryRecompile`| Запрос перекомпилируется, так как отсутствует без значительного выигрыша в производительности. |
| `PlanForcedByUser`| Пользователь вручную принудительного плана с помощью [sp_query_store_force_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) процедуры. |
| `PlanUnforcedByUser` | Пользователь вручную unforced плана с помощью [sp_query_store_unforce_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) процедуры. |

 Статистика в столбце сведений больше не показывать статистики плана выполнения (например, текущее время ЦП). Рекомендации более подробно создаются во время обнаружения регрессии и описывают почему [!INCLUDE[ssde_md](../../includes/ssde_md.md)] идентифицировать снижения производительности. Используйте `regressedPlanId` и `recommendedPlanId` запрос [Store запрос представления каталога](../../relational-databases/performance/how-query-store-collects-data.md) найти точное время выполнения плана статистики.

## <a name="examples-of-using-tuning-recommendations-information"></a>Примеры использования сведений о рекомендации настройки  

### <a name="example-1"></a>Пример 1
Получает созданный следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипт, который заставляет основательный план для любого заданного запроса:  
 
```sql
SELECT name, reason, score,
    JSON_VALUE(details, '$.implementationDetails.script') AS script,
    details.* 
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON(details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressed_plan_id int '$.regressedPlanId',
            last_good_plan_id int '$.recommendedPlanId') AS details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active';
```
### <a name="example-2"></a>Пример 2
Получает созданный следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипт, который заставляет основательный план для любого заданного запроса и Дополнительные сведения о Предполагаемый рост:

```sql
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressedPlanId int '$.regressedPlanId',
            recommendedPlanId int '$.recommendedPlanId',
            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,
            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float
          ) AS planForceDetails;
```

### <a name="example-3"></a>Пример 3
Получает созданный следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипт, который вызывает понижающую для любого заданного запроса и Дополнительные сведения, включающие текст запроса и планы запросов, хранящихся в Query Store:

```sql
WITH cte_db_tuning_recommendations
AS (SELECT reason,
        score,
        query_id,
        regressedPlanId,
        recommendedPlanId,
        current_state = JSON_VALUE(state, '$.currentValue'),
        current_state_reason = JSON_VALUE(state, '$.reason'),
        script = JSON_VALUE(details, '$.implementationDetails.script'),
        estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
        error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
    FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(Details, '$.planForceDetails')
    WITH ([query_id] int '$.queryId',
        regressedPlanId int '$.regressedPlanId',
        recommendedPlanId int '$.recommendedPlanId',
        regressedPlanErrorCount int,    
        recommendedPlanErrorCount int,
        regressedPlanExecutionCount int,
        regressedPlanCpuTimeAverage float,
        recommendedPlanExecutionCount int,
        recommendedPlanCpuTimeAverage float
        )
    )
SELECT qsq.query_id,
    qsqt.query_sql_text,
    dtr.*,
    CAST(rp.query_plan AS XML) AS RegressedPlan,
    CAST(sp.query_plan AS XML) AS SuggestedPlan
FROM cte_db_tuning_recommendations AS dtr
INNER JOIN sys.query_store_plan AS rp ON rp.query_id = dtr.query_id
    AND rp.plan_id = dtr.regressedPlanId
INNER JOIN sys.query_store_plan AS sp ON sp.query_id = dtr.query_id
    AND sp.plan_id = dtr.recommendedPlanId
INNER JOIN sys.query_store_query AS qsq ON qsq.query_id = rp.query_id
INNER JOIN sys.query_store_query_text AS qsqt ON qsqt.query_text_id = qsq.query_text_id;
```

Дополнительные сведения о функции JSON, которые могут использоваться для запроса значений в представлении рекомендации, см. в разделе [Поддержка JSON](../../relational-databases/json/index.md) в [!INCLUDE[ssde_md](../../includes/ssde_md.md)].
  
## <a name="permissions"></a>Разрешения  

Требуется `VIEW SERVER STATE` разрешение в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
Требуется `VIEW DATABASE STATE` разрешение для базы данных в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   

## <a name="see-also"></a>См. также  
 [Автоматическая настройка](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Поддержка JSON](../../relational-databases/json/index.md)
 
