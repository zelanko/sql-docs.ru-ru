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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c00bdd453bc4d1bf467b37aca3639eb43f55e022
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085793"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Запуски `UPDATE STATISTICS` для всех пользовательских и внутренних таблиц в текущей базе данных.  
  
Дополнительные сведения о `UPDATE STATISTICS`, см. в разделе [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Дополнительные сведения о статистике см. в статье [Статистика](../../relational-databases/statistics/statistics.md).  
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="arguments"></a>Аргументы  
`[ @resample = ] 'resample'` Указывает, что **sp_updatestats** будет использовать параметр RESAMPLE [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) инструкции. Если **'resample'** не указан, **sp_updatestats** обновляет статистику с помощью выборки по умолчанию. **Повторить выборку** — **varchar(8)** со значением по умолчанию "Нет".  
  
## <a name="remarks"></a>Примечания  
 **sp_updatestats** выполняет `UPDATE STATISTICS`, указав `ALL` ключевое слово, для всех пользовательских и внутренних таблиц в базе данных. sp_updatestats выводит сообщения о ходе своего выполнения. По завершении обновления выдается отчет о том, что обновление статистики произведено для всех таблиц.  
  
Процедура sp_updatestats обновляет статистику по отключенным некластеризованным индексам и не обновляет статистику по отключенным кластеризованным индексам.  
  
Для дисковых таблиц **sp_updatestats** обновляет статистику на основе **modification_counter** сведения в **sys.dm_db_stats_properties** представление каталога Обновление статистики, где был изменен по крайней мере одну строку. Статистика для таблиц, оптимизированных для памяти всегда обновляется при выполнении **sp_updatestats**. Поэтому не следует вызывать **sp_updatestats** чаще, чем необходимо.  
  
**sp_updatestats** можно запустить повторную компиляцию хранимых процедур или другого откомпилированного кода. Тем не менее **sp_updatestats** не может запустить повторную компиляцию, если только один план запроса для таблиц и индексов в них. Повторная компиляция в этих случаях будет не нужна даже при обновлении статистики.  
  
Для баз данных с уровнем совместимости ниже 90 при выполнении процедуры **sp_updatestats** не сохраняет последнее значение параметра NORECOMPUTE для заданной статистики. Для баз данных с уровнем совместимости 90 или выше sp_updatestats сохраняет последнее значение параметра NORECOMPUTE для заданной статистики. Дополнительные сведения об отключении и повторном включении обновления статистики см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли сервера или владельцем базы данных (**dbo**).  

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
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Системные хранимые процедуры](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
