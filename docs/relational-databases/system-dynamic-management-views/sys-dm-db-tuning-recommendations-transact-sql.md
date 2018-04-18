---
title: sys.dm_db_tuning_recommendations (Transact-SQL) | Документы Microsoft
description: Поиск потенциальных проблем с производительностью и рекомендуемые исправления в SQL Server и базы данных SQL Azure
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: fc933666e31c45fc78fb6d303ca1e7d3b5874d55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>sys.DM\_db\_СУБД\_рекомендации (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Возвращает подробные сведения о рекомендаций по настройке.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.

| **Имя столбца** | **Тип данных** | **Description** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Уникальное имя рекомендации. |
| **type** | **nvarchar(4000)** | Имя параметра автоматической настройки, созданного рекомендация, например, `FORCE_LAST_GOOD_PLAN` |
| **Причина** | **nvarchar(4000)** | Причина, почему был предоставлен этой рекомендации. |
| **Допустимые\_с момента** | **datetime2** | Эта рекомендация впервые был создан. |
| **последние\_обновления** | **datetime2** | Время последнего создания этой рекомендации. |
| **state** | **nvarchar(4000)** | Документ JSON, описывающий состояние рекомендаций. Доступны следующие поля:<br />-   `currentValue` -Текущее состояние в рекомендацию.<br />-   `reason` — Константа, которая описывает, почему рекомендуется в текущем состоянии.|
| **—\_исполняемый\_действие** | **бит** | 1 = рекомендации могут быть выполнены в базе данных через [!INCLUDE[tsql_md](../../includes/tsql_md.md)] сценария.<br />0 = рекомендаций не может быть выполнена для базы данных (например: рекомендации только или возвращенной информации) |
| **—\_revertable\_действия** | **бит** | 1 = автоматически отслеживания и вернуть ядром СУБД рекомендации.<br />0 = рекомендаций не может автоматически отслеживать и отменены. Большинство &quot;исполняемый&quot; действия будут &quot;revertable&quot;. |
| **выполнение\_действия\_запустить\_времени** | **datetime2** | Дата, когда применяется рекомендации. |
| **выполнение\_действия\_длительность** | **time** | Длительность выполнения действия. |
| **выполнение\_действия\_инициировал\_по** | **nvarchar(4000)** | `User` = Пользователь вручную принудительно плана в рекомендацию. <br /> `System` = Система автоматически применить рекомендации. |
| **выполнение\_действия\_инициировал\_времени** | **datetime2** | Дата применения рекомендаций. |
| **вернуть\_действия\_запустить\_времени** | **datetime2** | Дата, когда была отменена, рекомендации. |
| **вернуть\_действия\_длительность** | **time** | Длительность действия revert. |
| **вернуть\_действия\_инициировал\_по** | **nvarchar(4000)** | `User` = Пользователь вручную unforced рекомендуемые плана. <br /> `System` = Система автоматически возвращается рекомендации. |
| **вернуть\_действия\_инициировал\_времени** | **datetime2** | Дата, когда была отменена, рекомендации. |
| **Оценка** | **int** | Предполагаемое значение и влияние этой рекомендации по 0-100 масштаб (чем больше тем лучше) |
| **Подробные сведения** | **nvarchar(max)** | Документ JSON, который содержит дополнительные сведения о рекомендации. Доступны следующие поля:<br /><br />`planForceDetails`<br />-    `queryId` -запрос\_идентификатор регрессионных запросов.<br />-    `regressedPlanId` -plan_id регрессионных плана.<br />-   `regressedPlanExecutionCount` -Обнаружено число выполнений запроса с планом регрессионных перед регрессии.<br />-    `regressedPlanAbortedCount` -Число обнаружены ошибки во время выполнения регрессионных плана.<br />-    `regressedPlanCpuTimeAverage` -Среднее время ЦП, использованных запросом регрессионных до обнаружения регрессии.<br />-    `regressedPlanCpuTimeStddev` -Обнаружена стандартное отклонение время ЦП, затраченное на выполнение запроса регрессионных перед регрессии.<br />-    `recommendedPlanId` -plan_id плана, обязательно.<br />-   `recommendedPlanExecutionCount`— Число выполнений запроса с планом, обязательно до обнаружения регрессии.<br />-    `recommendedPlanAbortedCount` -Число обнаружены ошибки во время выполнения с планом, обязательно.<br />-    `recommendedPlanCpuTimeAverage` -Среднее время ЦП, затраченное на выполнение запроса, выполняться в плане, должно быть принудительно (вычисляется до обнаружения Регрессия).<br />-    `recommendedPlanCpuTimeStddev` Обнаружена стандартное отклонение время ЦП, затраченное на выполнение запроса регрессионных перед регрессии.<br /><br />`implementationDetails`<br />-  `method` -Метод, который следует использовать для устранения регрессии. Значение всегда равно `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql_md.md)] скрипт, который должен быть выполнен для принудительного плана, рекомендуется. |
  
## <a name="remarks"></a>Замечания  
 Сведения, возвращаемые функцией `sys.dm_db_tuning_recommendations` обновляется, когда компонент database engine определяет потенциальные снижением производительности запросов и не сохраняется. Рекомендации хранится только до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускается. Администраторы базы данных должны периодически делать резервные копии рекомендации по настройке, если необходимо сохранить их после перезагрузки сервера. 

 `currentValue` в поле `state` столбец может иметь следующие значения:
 | Состояние | Описание |
 |--------|-------------|
 | `Active` | Рекомендуется активных и еще не установлены. Пользователь может выполнить скрипт рекомендаций и выполнить его вручную. |
 | `Verifying` | Рекомендации по применяется [!INCLUDE[ssde_md](../../includes/ssde_md.md)] и процесс проверки внутреннего сравнивает производительность форсированном плане со сниженной производительностью плана. |
 | `Success` | Рекомендация успешно применены. |
 | `Reverted` | Рекомендация отменена, так как существуют не значительный прирост производительности. |
 | `Expired` | Рекомендация истек и не может применяться больше. |

Документ JSON в `state` столбец содержит причину, которая описывает, почему содержит рекомендации в текущем состоянии. Может принимать следующие значения в поле Причина: 

| Причина | Описание |
|--------|-------------|
| `SchemaChanged` | Истек срок действия рекомендаций, из-за изменения схемы таблицы, на которую указывает ссылка. |
| `StatisticsChanged`| Истек срок действия рекомендаций из-за изменения статистики по указанной таблице. |
| `ForcingFailed` | Рекомендуемый план нельзя принудительно применить на запросе. Найти `last_force_failure_reason` в [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) представление, чтобы найти причину сбоя. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` параметр будет отключен пользователем во время процесса проверки. Включить `FORCE_LAST_GOOD_PLAN` с помощью [ALTER базы данных ЗАДАЙТЕ AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) инструкции или принудительное план вручную с помощью сценария в `[details]` столбца. |
| `UnsupportedStatementType` | План нельзя принудительно применить к запросу. Примеры запросов, не поддерживается, курсоры и `INSERT BULK` инструкции. |
| `LastGoodPlanForced` | Рекомендация успешно применены. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] определить потенциальные снижения производительности, но `FORCE_LAST_GOOD_PLAN` параметр не включен, читайте в [ALTER AUTOMATIC_TUNING базы данных ЗАДАЙТЕ &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Применить рекомендацию вручную или включить `FORCE_LAST_GOOD_PLAN` параметр. |
| `VerificationAborted`| Процесс проверки прервана из-за перезагрузки или при очистке хранилища запросов. |
| `VerificationForcedQueryRecompile`| Запрос перекомпилируется, так как отсутствует без значительного выигрыша в производительности. |
| `PlanForcedByUser`| Пользователь вручную принудительно плана с помощью [sp_query_store_force_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) процедуры. |
| `PlanUnforcedByUser` | Пользователь вручную непринудительно плана с помощью [sp_query_store_unforce_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) процедуры. |

 Статистика в столбце сведения больше не показывать статистику плана выполнения (например, текущее время ЦП). Подробные сведения по рекомендации выполненные во время обнаружения регрессии и описывают, почему [!INCLUDE[ssde_md](../../includes/ssde_md.md)] идентифицировать снижения производительности. Используйте `regressedPlanId` и `recommendedPlanId` запрос [представления каталога хранилища запросов](../../relational-databases/performance/how-query-store-collects-data.md) найти точное время выполнения плана статистики.

## <a name="using-tuning-recommendations-information"></a>С помощью настройки сведения о рекомендациях  
 Чтобы получить скрипт T-SQL, который исправит проблему, можно использовать следующий запрос:  
 
```
SELECT name, reason, score,
        JSON_VALUE(details, '$.implementationDetails.script') as script,
        details.* 
FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(details, '$.planForceDetails')
                WITH (  query_id int '$.queryId',
                        regressed_plan_id int '$.regressedPlanId',
                        last_good_plan_id int '$.recommendedPlanId') as details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active'
```
  
 Дополнительные сведения о функции JSON, которые могут использоваться для запроса значений в представлении рекомендации см. в разделе [Поддержка JSON](../../relational-databases/json/index.md) в [!INCLUDE[ssde_md](../../includes/ssde_md.md)].
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
 [Автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Поддержка JSON](../../relational-databases/json/index.md)
 
