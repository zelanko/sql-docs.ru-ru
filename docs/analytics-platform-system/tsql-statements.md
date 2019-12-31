---
title: Инструкции T-SQL
description: Инструкции T-SQL для аналитической системы платформы (ТД) SQL Server Parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ce80d7a27384f628af02bfa58abcaa351b569d56
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399812"
---
# <a name="t-sql-statements-for-parallel-data-warehouse"></a>Инструкции T-SQL для параллельного хранилища данных
Инструкции Transact-SQL (T-SQL) для аналитической системы платформы (ТД) SQL Server Parallel Data Warehouse (PDW).

## <a name="data-definition-language-ddl-statements"></a>Инструкции языка описания данных DDL
* [ИЗМЕНЕНИЕ БАЗЫ ДАННЫХ](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)
* [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md)
* [ИЗМЕНЕНИЕ ПРОЦЕДУРЫ](../t-sql/statements/alter-procedure-transact-sql.md)
* [ИЗМЕНЕНИЕ СХЕМЫ](../t-sql/statements/alter-schema-transact-sql.md)
* [ИЗМЕНЕНИЕ ТАБЛИЦЫ](../t-sql/statements/alter-table-transact-sql.md)
* [СОЗДАТЬ ИНДЕКС COLUMNSTORE](../t-sql/statements/create-columnstore-index-transact-sql.md)
* [СОЗДАНИЕ БАЗЫ ДАННЫХ](../t-sql/statements/create-database-azure-sql-data-warehouse.md)
* [СОЗДАНИЕ УЧЕТНЫХ ДАННЫХ ДЛЯ БАЗЫ ДАННЫХ](../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [СОЗДАНИЕ ВНЕШНЕГО ИСТОЧНИКА ДАННЫХ](../t-sql/statements/create-external-data-source-transact-sql.md)
* [СОЗДАНИЕ ФОРМАТА ВНЕШНЕГО ФАЙЛА](../t-sql/statements/create-external-file-format-transact-sql.md)
* [СОЗДАТЬ ВНЕШНЮЮ ТАБЛИЦУ](../t-sql/statements/create-external-table-transact-sql.md)
* [СОЗДАНИЕ ФУНКЦИИ](../t-sql/statements/create-function-sql-data-warehouse.md)
* [СОЗДАТЬ ИНДЕКС](../t-sql/statements/create-index-transact-sql.md)
* [СОЗДАТЬ ПРОЦЕДУРУ](../t-sql/statements/create-procedure-transact-sql.md)
* [СОЗДАТЬ СХЕМУ](../t-sql/statements/create-schema-transact-sql.md)
* [СОЗДАНИЕ СТАТИСТИКИ](../t-sql/statements/create-statistics-transact-sql.md)
* [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md)
* [CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)
* [СОЗДАТЬ ПРЕДСТАВЛЕНИЕ](../t-sql/statements/create-view-transact-sql.md)
* [УДАЛИТЬ ВНЕШНИЙ ИСТОЧНИК ДАННЫХ](../t-sql/statements/drop-external-data-source-transact-sql.md)
* [УДАЛИТЬ ФОРМАТ ВНЕШНЕГО ФАЙЛА](../t-sql/statements/drop-external-file-format-transact-sql.md)
* [УДАЛИТЬ ВНЕШНЮЮ ТАБЛИЦУ](../t-sql/statements/drop-external-table-transact-sql.md)
* [DROP INDEX](../t-sql/statements/drop-index-transact-sql.md)
* [УДАЛИТЬ ПРОЦЕДУРУ](../t-sql/statements/drop-procedure-transact-sql.md)
* [УДАЛИТЬ СТАТИСТИКУ](../t-sql/statements/drop-statistics-transact-sql.md)
* [УДАЛИТЬ ТАБЛИЦУ](../t-sql/statements/drop-table-transact-sql.md)
* [УДАЛИТЬ СХЕМУ](../t-sql/statements/drop-schema-transact-sql.md)
* [УДАЛИТЬ ПРЕДСТАВЛЕНИЕ](../t-sql/statements/drop-view-transact-sql.md)
* [ИМЕНИ](../t-sql/statements/rename-transact-sql.md)
* [TRUNCATE TABLE](../t-sql/statements/truncate-table-transact-sql.md)
* [ОБНОВИТЬ СТАТИСТИКУ](../t-sql/statements/update-statistics-transact-sql.md)

## <a name="data-manipulation-language-dml-statements"></a>Инструкции языка обработки данных DML
* [УДАЛЕН](../t-sql/statements/delete-transact-sql.md)
* [ВСТАВЛЯЕТ](../t-sql/statements/insert-transact-sql.md)
* [ОБНОВЛЯЮТ](../t-sql/queries/update-transact-sql.md)

## <a name="database-console-commands"></a>Команды консоли базы данных
* [DBCC DROPCLEANBUFFERS](../t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql.md)
* [DBCC FREEPROCCACHE](https://msdn.microsoft.com/library/mt204018.aspx)
* [DBCC SHRINKLOG](https://msdn.microsoft.com/library/mt204020.aspx)
* [DBCC PDW_SHOWEXECUTIONPLAN](https://msdn.microsoft.com/library/mt204017.aspx)
* [DBCC PDW_SHOWPARTITIONSTATS](https://msdn.microsoft.com/library/mt204013.aspx)
* [DBCC PDW_SHOWSPACEUSED](../t-sql/database-console-commands/dbcc-pdw-showspaceused-transact-sql.md)
* [DBCC SHOW_STATISTICS](https://msdn.microsoft.com/library/mt204043.aspx)

## <a name="query-statements"></a>Инструкции запросов
* [МЕТЬТЕ](../t-sql/queries/select-transact-sql.md)
* [С common_table_expression](../t-sql/queries/with-common-table-expression-transact-sql.md)
* [EXCEPT и INTERSECT](../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)
* [ОБЪЯСНИТ](../t-sql/queries/explain-transact-sql.md)
* [От](../t-sql/queries/from-transact-sql.md)
* [Использование PIVOT и UNPIVOT](../t-sql/queries/from-using-pivot-and-unpivot.md)
* [ГРУППИРОВАТЬ ПО](../t-sql/queries/select-group-by-transact-sql.md)
* [CAPS](../t-sql/queries/select-having-transact-sql.md)
* [ORDER BY](../t-sql/queries/select-order-by-clause-transact-sql.md)
* [ФУНКЦИЮ](../t-sql/queries/option-clause-transact-sql.md)
* [НАБОРОВ](../t-sql/language-elements/set-operators-union-transact-sql.md)
* [КОТОРОМУ](../t-sql/queries/where-transact-sql.md)
* [Вверх](../t-sql/queries/top-transact-sql.md)
* [Псевдонимы](../t-sql/queries/aliasing-azure-sql-data-warehouse-parallel-data-warehouse.md)
* [Условие поиска](../t-sql/queries/search-condition-transact-sql.md)
* [Вложенные запросы](../t-sql/queries/subqueries-azure-sql-data-warehouse-parallel-data-warehouse.md)

## <a name="security-statements"></a>Инструкции по безопасности
* Разрешения: [GRANT](../t-sql/statements/grant-transact-sql.md), [DENY](../t-sql/statements/deny-transact-sql.md), [REVOKE](../t-sql/statements/revoke-transact-sql.md)
* [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md)
* [ИЗМЕНЕНИЕ СЕРТИФИКАТА](../t-sql/statements/alter-certificate-transact-sql.md)
* [ИЗМЕНЕНИЕ КЛЮЧА ШИФРОВАНИЯ БАЗЫ ДАННЫХ](../t-sql/statements/alter-database-encryption-key-transact-sql.md)
* [ИЗМЕНЕНИЕ ИМЕНИ ВХОДА](../t-sql/statements/alter-login-transact-sql.md)
* [ИЗМЕНЕНИЕ ГЛАВНОГО КЛЮЧА](../t-sql/statements/alter-master-key-transact-sql.md)
* [ИЗМЕНЕНИЕ РОЛИ](../t-sql/statements/alter-role-transact-sql.md)
* [ИЗМЕНЕНИЕ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/alter-user-transact-sql.md)
* [СЕРТИФИКАТ РЕЗЕРВНОЙ КОПИИ](../t-sql/statements/backup-certificate-transact-sql.md)
* [ЗАКРЫТЬ ГЛАВНЫЙ КЛЮЧ](../t-sql/statements/close-master-key-transact-sql.md)
* [СОЗДАТЬ СЕРТИФИКАТ](../t-sql/statements/create-certificate-transact-sql.md)
* [СОЗДАНИЕ КЛЮЧА ШИФРОВАНИЯ БАЗЫ ДАННЫХ](../t-sql/statements/create-database-encryption-key-transact-sql.md)
* [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)
* [СОЗДАТЬ ГЛАВНЫЙ КЛЮЧ](../t-sql/statements/create-master-key-transact-sql.md)
* [СОЗДАНИЕ РОЛИ](../t-sql/statements/create-role-transact-sql.md)
* [СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/create-user-transact-sql.md)
* [УДАЛИТЬ СЕРТИФИКАТ](../t-sql/statements/drop-certificate-transact-sql.md)
* [УДАЛИТЬ КЛЮЧ ШИФРОВАНИЯ БАЗЫ ДАННЫХ](../t-sql/statements/drop-database-encryption-key-transact-sql.md)
* [УДАЛИТЬ ИМЯ ДЛЯ ВХОДА](../t-sql/statements/drop-login-transact-sql.md)
* [УДАЛИТЬ ГЛАВНЫЙ КЛЮЧ](../t-sql/statements/drop-master-key-transact-sql.md)
* [УДАЛИТЬ РОЛЬ](../t-sql/statements/drop-role-transact-sql.md)
* [УДАЛИТЬ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/drop-user-transact-sql.md)
* [ОТКРЫТЬ ГЛАВНЫЙ КЛЮЧ](../t-sql/statements/open-master-key-transact-sql.md)

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные справочные сведения см. в разделе [элементы языка t-SQL](tsql-language-elements.md) и [системные представления t-SQL](tsql-system-views.md).

<!--Image references-->

<!--Article references-->

<!--MSDN references-->

<!--Other Web references-->
