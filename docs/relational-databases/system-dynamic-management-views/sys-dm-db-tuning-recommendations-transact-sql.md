---
title: sys.dm_db_tuning_recommendations (Трансакт-СЗЛ) Документы Майкрософт
description: Узнайте, как найти потенциальные проблемы с производительностью и рекомендуемые исправления в базе данных S'L Server и Azure S'L
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
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e8c18ce07ba5e36dcbdb5750db77edf17495c7b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285554"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>рекомендации\_по настройке\_sys.dm\_db (Трансакт-СЗЛ)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Возвращает подробную информацию о рекомендациях по настройке.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать раскрытия этой информации, отфильтровывается каждая строка, содержащая данные, не принадлежащие подключенным арендатору.

| **Название колонки** | **Тип данных** | **Описание** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Уникальное название рекомендации. |
| **тип** | **nvarchar(4000)** | Название опции автоматической настройки, которая подготовила рекомендацию, например,`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Причина, по которой была предоставлена эта рекомендация. |
| **действителен\_с тех пор, как** | **datetime2** | Впервый раз эта рекомендация была создана. |
| **последнее\_обновление** | **datetime2** | Последний раз эта рекомендация была создана. |
| **Государства** | **nvarchar(4000)** | Документ JSON, описывающий состояние рекомендации. Доступны следующие поля:<br />-   `currentValue`- текущее состояние рекомендации.<br />-   `reason`- постоянная, которая описывает, почему рекомендация находится в текущем состоянии.|
| **является\_исполняемым действием\_** | **bit** | 1 - Рекомендация может быть выполнена в отношении базы данных с помощью [!INCLUDE[tsql_md](../../includes/tsql-md.md)] сценария.<br />0 - Рекомендация не может быть выполнена в отношении базы данных (например: только информация или возвращенная рекомендация) |
| **является\_повторное\_действие** | **bit** | 1 - Рекомендация может быть автоматически проверена и возвращена движком базы данных.<br />0 - Рекомендация не может быть автоматически проверена и возвращена. Большинство &quot;исполняемых&quot; действий будут &quot;повторно.&quot; |
| **\_выполнить\_\_время начала действия** | **datetime2** | Дата применения рекомендации. |
| **\_выполнить\_продолжительность действия** | **time** | Длительность выполнения действия. |
| **\_выполнить\_\_действия, инициированные** | **nvarchar(4000)** | `User`Пользователь вручную принудил план в рекомендации. <br /> `System`Система автоматически применяет рекомендацию. |
| **\_выполнить\_\_время инициированного действия** | **datetime2** | Дата применения рекомендации. |
| **время\_начала\_\_действия** | **datetime2** | Дата возврата рекомендации. |
| **вернуть\_продолжительность действия\_** | **time** | Длительность действия возврата. |
| **вернуть\_действие,\_инициированное\_** | **nvarchar(4000)** | `User`Пользователь вручную невынужденный рекомендуемый план. <br /> `System`Система автоматически возвращает рекомендацию. |
| **вернуть\_\_действие,\_инициированное временем** | **datetime2** | Дата возврата рекомендации. |
| **Оценка по** | **INT** | Ориентировочная стоимость/воздействие на эту рекомендацию по шкале 0-100 (чем больше, тем лучше) |
| **Детали** | **nvarchar (макс)** | Документ JSON, содержащий более подробную информацию о рекомендации. Доступны следующие поля:<br /><br />`planForceDetails`<br />-    `queryId`- идентификатор\_запроса регрессированного запроса.<br />-    `regressedPlanId`- plan_id регрессного плана.<br />-   `regressedPlanExecutionCount`- Количество выполнения запроса с регрессированным планом до обнаружения регрессии.<br />-    `regressedPlanAbortedCount`- Количество обнаруженных ошибок при выполнении регрессированного плана.<br />-    `regressedPlanCpuTimeAverage`- Среднее время процессора (в микро секундах), потребляемых регрессированным запросом до обнаружения регрессии.<br />-    `regressedPlanCpuTimeStddev`- Стандартное отклонение времени процессора, потребляемого регрессным запросом до обнаружения регрессии.<br />-    `recommendedPlanId`- plan_id плана, который должен быть вынужденным.<br />-   `recommendedPlanExecutionCount`- Количество выполнения запроса с планом, который должен быть вынужден до обнаружения регрессии.<br />-    `recommendedPlanAbortedCount`- Количество обнаруженных ошибок при выполнении плана, которые должны быть вынуждены.<br />-    `recommendedPlanCpuTimeAverage`- Среднее время процессора (в микро секундах), потребляемый запросом, выполняемым с планом, который должен быть вынужден (рассчитан до обнаружения регрессии).<br />-    `recommendedPlanCpuTimeStddev`Стандартное отклонение времени процессора, потребляемого регрессным запросом до обнаружения регрессии.<br /><br />`implementationDetails`<br />-  `method`- Метод, который должен быть использован для коррекции регрессии. Значение всегда `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]скрипт, который должен быть выполнен, чтобы заставить рекомендуемый план. |
  
## <a name="remarks"></a>Remarks  
 Информация, `sys.dm_db_tuning_recommendations` возвращенная, обновляется, когда движок базы данных определяет потенциальную регрессию производительности запроса, и не сохраняется. Рекомендации сохраняются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только до тех пор, пока не будет перезапущен. Администраторы баз данных должны периодически делать резервные копии рекомендации по настройке, если они хотят сохранить ее после рециркуляции сервера. 

 `currentValue`поле в `state` столбце может иметь следующие значения:
 
 | Состояние | Описание |
 |--------|-------------|
 | `Active` | Рекомендация активна и еще не применяется. Пользователь может взять сценарий рекомендаций и выполнить его вручную. |
 | `Verifying` | Рекомендация применяется путем, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] и процесс внутренней проверки сравнивает выполнение принудительного плана с регрессным планом. |
 | `Success` | Рекомендация успешно применяется. |
 | `Reverted` | Рекомендация возвращается, поскольку нет значительных результатов в области производительности. |
 | `Expired` | Рекомендация истекла и больше не может быть применена. |

Документ JSON `state` в столбце содержит причину, по которой описывается, почему рекомендация находится в текущем состоянии. Значения в поле причины могут быть: 

| Причина | Описание |
|--------|-------------|
| `SchemaChanged` | Рекомендация истекла из-за изменения схемы справочной таблицы. Новая рекомендация будет создана, если на новой схеме будет обнаружена регрессия нового плана запроса. |
| `StatisticsChanged`| Срок действия рекомендации истек из-за изменения статистики в справочной таблице. Новая рекомендация будет создана, если будет обнаружена регрессия нового плана запроса на основе новых статистических данных. |
| `ForcingFailed` | Рекомендуемый план не может быть принудительно принудить к запросу. Найти `last_force_failure_reason` в [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) вид, чтобы найти причину сбоя. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`опция отключена пользователем во время процесса проверки. Включить `FORCE_LAST_GOOD_PLAN` опцию с использованием ALTER DATABASE SET AUTOMATIC_TUNING &#40;&#41;заявление [Transact-S'L](../../t-sql/statements/alter-database-transact-sql-set-options.md) или заставить план вручную использовать скрипт в `[details]` столбце. |
| `UnsupportedStatementType` | План не может быть принудить к запросу. Примерами неподдерживаемых запросов являются `INSERT BULK` курсоры и оператора. |
| `LastGoodPlanForced` | Рекомендация успешно применяется. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]определили потенциальную регрессию производительности, но `FORCE_LAST_GOOD_PLAN` опция не включена - с&#41;&#40;[AUTOMATIC_TUNINGм. ](../../t-sql/statements/alter-database-transact-sql-set-options.md) Применяйте рекомендации `FORCE_LAST_GOOD_PLAN` вручную или включите опцию. |
| `VerificationAborted`| Процесс проверки прерывается из-за перезагрузки или очистки магазина запросов. |
| `VerificationForcedQueryRecompile`| Запрос перекомпилируется, поскольку существенного улучшения производительности не наблюдается. |
| `PlanForcedByUser`| Пользователь вручную принудил план, используя sp_query_store_force_plan &#40;процедуру [&#41;Transact-S'L.](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) Движок базы данных не будет применять рекомендацию, если пользователь явно решил заставить какой-либо план. |
| `PlanUnforcedByUser` | Пользователь вручную не вынужденный план, используя sp_query_store_unforce_plan &#40;процедуру [&#41;Transact-S'L.](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) Поскольку пользователь явно вернул рекомендуемый план, движок базы данных будет продолжать использовать текущий план и генерировать новую рекомендацию, если в будущем произойдет регрессия плана. |

 Статистика в столбце деталей не показывает статистику плана выполнения (например, текущее время процессора). Детали рекомендации принимаются во время обнаружения регрессии и описывают, почему [!INCLUDE[ssde_md](../../includes/ssde_md.md)] выявлено регрессии производительности. `regressedPlanId` Используйте `recommendedPlanId` и запрашивать [представления каталога «Магазин запросов»,](../../relational-databases/performance/how-query-store-collects-data.md) чтобы найти точную статистику плана выполнения.

## <a name="examples-of-using-tuning-recommendations-information"></a>Примеры использования информации о рекомендациях по настройке  

### <a name="example-1"></a>Пример 1
Ниже приводится [!INCLUDE[tsql](../../includes/tsql-md.md)] сгенерированный скрипт, который заставляет хороший план для любого заданного запроса:  
 
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
Следующий получает [!INCLUDE[tsql](../../includes/tsql-md.md)] сгенерированный скрипт, который заставляет хороший план для любого данного запроса и дополнительную информацию о предполагаемой прибыли:

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
Следующий получает [!INCLUDE[tsql](../../includes/tsql-md.md)] сгенерированный скрипт, который заставляет хороший план для любого заданного запроса и дополнительную информацию, которая включает текст запроса и планы запросов, хранящиеся в Магазине запросов:

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

Для получения дополнительной информации о функциях JSON, которые могут быть использованы [!INCLUDE[ssde_md](../../includes/ssde_md.md)]для запроса значений в представлении рекомендаций, см. [JSON Support](../../relational-databases/json/index.md)
  
## <a name="permissions"></a>Разрешения  

Требуется `VIEW SERVER STATE` [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]разрешение в .   
Требуется `VIEW DATABASE STATE` разрешение для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]базы данных в .   

## <a name="see-also"></a>См. также:  
 [Автоматическая настройка](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;&#41;"Трансакт-СЗЛ"](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;&#41;"Трансакт-СЗЛ"](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Поддержка JSON](../../relational-databases/json/index.md)
 
