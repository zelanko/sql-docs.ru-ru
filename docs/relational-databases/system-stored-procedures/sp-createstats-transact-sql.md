---
title: sp_createstats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_createstats_TSQL
- sp_createstats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_createstats
ms.assetid: 8204f6f2-5704-40a7-8d51-43fc832eeb54
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 75e05e36dfea3a36fa01d08ca79b22c3abb7e2c4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555164"
---
# <a name="spcreatestats-transact-sql"></a>Хранимая процедура sp_createstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Вызовы [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) инструкцию, чтобы создать статистику по отдельным столбцам для столбцов, которые не входят в первом столбце объекта статистики. Создание статистики по отдельным столбцам увеличивает число гистограмм, что может улучшить оценку количества элементов, усовершенствовать планы запросов и повысить производительность запросов. Первый столбец объекта статистики содержит гистограмму, а прочие — не содержат.  
  
 Процедура sp_createstats полезна для таких задач, как тестирование производительности, когда существенно важно время выполнения запросов и недопустимо ожидание построения статистики по отдельным столбцам оптимизатором запросов. В большинстве случаев нет необходимости использовать процедуру sp_createstats; планы запроса, оптимизатор создает статистику по отдельным столбцам для усовершенствования запросов, когда **AUTO_CREATE_STATISTICS** включен параметр.  
  
 Дополнительные сведения о статистике см. в статье [Статистика](../../relational-databases/statistics/statistics.md). Дополнительные сведения о создании статистики по отдельным столбцам см. в разделе **AUTO_CREATE_STATISTICS** в диалоговом окне [параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_createstats   
    [   [ @indexonly =   ] { 'indexonly'   | 'NO' } ]   
    [ , [ @fullscan =    ] { 'fullscan'    | 'NO' } ]   
    [ , [ @norecompute = ] { 'norecompute' | 'NO' } ]  
    [ , [ @incremental = ] { 'incremental' | 'NO' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@indexonly=** ] **«indexonly»**  
 Создает статистику только по столбцам, которые входят в существующий индекс, причем ни один из столбцов не должен быть первым столбцом в определении индекса. **indexonly** — **char(9)**. Значение по умолчанию — NO.  
  
 [  **@fullscan=** ] **«fullscan»**  
 Использует [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) инструкции с **FULLSCAN** параметр. **FULLSCAN** — **char(9)**.  Значение по умолчанию — NO.  
  
 [  **@norecompute=** ] **«norecompute»**  
 Использует [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) инструкции с **NORECOMPUTE** параметр. **NORECOMPUTE** — **char(12)**.  Значение по умолчанию — NO.  
  
 [  **@incremental=** ] **«добавочное»**  
 Использует [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) инструкции с **INCREMENTAL = ON** параметр. **Добавочные** — **char(12)**.  Значение по умолчанию — NO.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Каждая новая статистика имеет имя, совпадающее со столбцом, по которому она создается.  
  
## <a name="remarks"></a>Примечания  
 Хранимая процедура sp_createstats не создает и не обновляет статистику по столбцам, в которых является первым столбцом в существующем объекте статистики;  Это включает в себя первый столбец статистики для индексов, столбцы с статистику по отдельным столбцам, созданным параметром AUTO_CREATE_STATISTICS и первый столбец статистики, созданные с помощью инструкции CREATE STATISTICS. Хранимая процедура sp_createstats не создает статистику в первых столбцах отключенных индексов, если только этот столбец не используется другим включенным индексом. Хранимая процедура sp_createstats не создает статистику для таблиц с отключенным кластеризованным индексом.  
  
 Если таблица содержит набор столбцов, то хранимая процедура sp_createstats не создает статистику по разреженным столбцам. Дополнительные сведения о наборах столбцов и разреженные столбцы, см. в разделе [использование наборов столбцов](../../relational-databases/tables/use-column-sets.md) и [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-single-column-statistics-on-all-eligible-columns"></a>A. Создание статистики по отдельным столбцам для всех подходящих столбцов  
 В следующем примере создается статистика по отдельным столбцам для всех подходящих столбцов в базе данных.  
  
```  
EXEC sp_createstats;  
GO  
```  
  
### <a name="b-create-single-column-statistics-on-all-eligible-index-columns"></a>Б. Создание статистики по отдельным столбцам для всех подходящих столбцов индекса  
 В следующем примере создается статистика по отдельным столбцам для всех подходящих столбцов, которые включены в индекс, но не являются первыми в индексе.  
  
```  
EXEC sp_createstats 'indexonly';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
