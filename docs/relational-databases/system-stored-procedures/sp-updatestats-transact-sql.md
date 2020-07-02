---
title: sp_updatestats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4449e2a518ab1bfd12563070a80514d890eae48c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723061"
---
# <a name="sp_updatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Выполняется `UPDATE STATISTICS` для всех определяемых пользователем и внутренних таблиц в текущей базе данных.  
  
Дополнительные сведения о см `UPDATE STATISTICS` . в разделе [UPDATE STATISTICS &#40;TRANSACT-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Дополнительные сведения о статистике см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).  
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="arguments"></a>Аргументы  
`[ @resample = ] 'resample'`Указывает, что **sp_updatestats** будет использовать параметр ресамплинг инструкции [Update Statistics](../../t-sql/statements/update-statistics-transact-sql.md) . Если параметр **"ресамплинг"** не указан, **sp_updatestats** обновляет статистику с использованием выборки по умолчанию. **ресамплинг** имеет тип **varchar (8)** со ЗНАЧЕНИЕМ по умолчанию No.  
  
## <a name="remarks"></a>Примечания  
 **sp_updatestats** выполняется `UPDATE STATISTICS` путем указания `ALL` ключевого слова для всех определяемых пользователем и внутренних таблиц в базе данных. sp_updatestats отображает сообщения, указывающие ход выполнения. По завершении обновления выдается отчет о том, что обновление статистики произведено для всех таблиц.  
  
**sp_updatestats** обновляет статистику отключенных некластеризованных индексов и не обновляет статистику отключенных кластеризованных индексов.  
  
Для дисковых таблиц **sp_updatestats** обновляет статистику на основе сведений о **modification_counter** в представлении каталога **sys. dm_db_stats_properties** , обновляя статистику, когда по крайней мере одна строка была изменена. Статистика для таблиц, оптимизированных для памяти, всегда обновляется при выполнении **sp_updatestats**. Поэтому не выполняйте **sp_updatestats** больше, чем требуется.  
  
**sp_updatestats** может активировать перекомпиляцию хранимых процедур или другого скомпилированного кода. Однако **sp_updatestats** может не вызвать перекомпиляцию, если для таблиц, на которые имеются ссылки, и индексов на них доступен только один план запроса. Повторная компиляция в этих случаях будет не нужна даже при обновлении статистики.  
  
Для баз данных с уровнем совместимости, указанным ниже 90, при исполнении **sp_updatestats** не сохраняются последние значения NORECOMPUTE для конкретной статистики. Для баз данных с уровнем совместимости 90 или выше sp_updatestats сохраняет последнюю версию параметра NORECOMPUTE для конкретной статистики. Дополнительные сведения об отключении и повторном включении обновления статистики см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Разрешения  

Для запуска **sp_updatestats**пользователь должен быть владельцем базы данных (а `dbo` не только членом роли `db_owner` ) или членом предопределенной роли сервера sysadmin.

## <a name="examples"></a>Примеры  
В следующем примере обновляется статистика для таблиц в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  

## <a name="automatic-index-and-statistics-management"></a>Автоматическое управление индексами и статистикой
Используйте такие решения, как [Адаптивная дефрагментация индексов](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), чтобы автоматически управлять дефрагментацией индексов и обновлениями статистики для одной базы данных или нескольких. Эта процедура автоматически выбирает, следует ли перестроить или реорганизовать индекс, сверяясь с уровнем фрагментации и другими параметрами, и обновляет статистику на основе линейных пороговых значений.

## <a name="see-also"></a>См. также  
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Создание статистики &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [Удаление статистики &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [Обновление статистики &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Системные хранимые процедуры](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
