---
description: Хранимая процедура sp_createstats (Transact-SQL)
title: sp_createstats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_createstats_TSQL
- sp_createstats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_createstats
ms.assetid: 8204f6f2-5704-40a7-8d51-43fc832eeb54
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7af34bd1bbe065012b18826f7edaec31940d1e50
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466875"
---
# <a name="sp_createstats-transact-sql"></a>Хранимая процедура sp_createstats (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Вызывает инструкцию [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) для создания статистики по отдельным столбцам для столбцов, которые еще не являются первым столбцом в объекте статистики. Создание статистики по отдельным столбцам увеличивает число гистограмм, что может улучшить оценку количества элементов, усовершенствовать планы запросов и повысить производительность запросов. Первый столбец объекта статистики содержит гистограмму, а прочие — не содержат.  
  
 Процедура sp_createstats полезна для таких задач, как тестирование производительности, когда существенно важно время выполнения запросов и недопустимо ожидание построения статистики по отдельным столбцам оптимизатором запросов. В большинстве случаев нет необходимости использовать sp_createstats. Оптимизатор запросов создает статистику по одному столбцу, если это необходимо для улучшения планов запросов, если параметр **AUTO_CREATE_STATISTICS** имеет значение ON.  
  
 Дополнительные сведения о статистике см. в статье [Статистика](../../relational-databases/statistics/statistics.md). Дополнительные сведения о формировании статистики по отдельным столбцам см. в описании параметра **AUTO_CREATE_STATISTICS** в разделе [Параметры инструкции ALTER DATABASE SET &#40;&#41;Transact-SQL](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
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
`[ @indexonly = ] 'indexonly'` Создает статистику только по столбцам, которые находятся в существующем индексе и не являются первым столбцом в определении индекса. **индексонли** имеет **тип char (9)**. Значение по умолчанию — NO.  
  
`[ @fullscan = ] 'fullscan'` Использует инструкцию [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) с параметром **FULLSCAN** . **FULLSCAN** имеет **тип char (9)**.  Значение по умолчанию — NO.  
  
`[ @norecompute = ] 'norecompute'` Использует инструкцию [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) с параметром **NORECOMPUTE** . **NORECOMPUTE** имеет **тип char (12)**.  Значение по умолчанию — NO.  
  
`[ @incremental = ] 'incremental'` Использует инструкцию [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) с параметром **инкремент = on** . **Добавочный** — **char (12)**.  Значение по умолчанию — NO.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Каждая новая статистика имеет имя, совпадающее со столбцом, по которому она создается.  
  
## <a name="remarks"></a>Комментарии  
 sp_createstats не создает или не обновляет статистику по столбцам, которые являются первым столбцом в существующем объекте статистики;  Сюда входит первый столбец статистики, созданный для индексов, столбцы с статистикой по отдельным столбцам, созданные с помощью AUTO_CREATE_STATISTICS параметр, и первый столбец статистики, созданный с помощью инструкции CREATE STATISTICS. sp_createstats не создает статистику по первым столбцам отключенных индексов, если этот столбец не используется в другом включенном индексе. sp_createstats не создает статистику по таблицам с отключенным кластеризованным индексом.  
  
 Если таблица содержит набор столбцов, то хранимая процедура sp_createstats не создает статистику по разреженным столбцам. Дополнительные сведения о наборах столбцов и разреженных столбцах см. в разделе [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md) и [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
