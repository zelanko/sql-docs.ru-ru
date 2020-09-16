---
description: Включение Stretch Database для таблицы
title: Включение Stretch Database для таблицы
ms.date: 08/05/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, enabling table
- enabling table for Stretch Database
ms.assetid: de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 10f267dc42c7626ad89b576b00e2b80a07dae427
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454403"
---
# <a name="enable-stretch-database-for-a-table"></a>Включение Stretch Database для таблицы
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


  Чтобы настроить таблицу для Stretch Database, в SQL Server Management Studio выберите для нужной таблицы команду **Растяжение | Включить** , чтобы открыть мастер **Включение растяжения для таблицы** . Stretch Database для таблицы можно включить также с помощью Transact-SQL. Либо можно создать новую таблицу, уже настроенную для Stretch Database.  
  
-   Если холодные данные хранятся в отдельной таблице, эту таблицу можно перенести полностью.  
  
-   Если таблица содержит как горячие, так и холодные данные, строки для переноса можно выбрать с помощью функции фильтров.    
 
 **Предварительные требования**. Если при выборе **Растяжение | Включить** для таблицы вы не включили Stretch Database для базы данных, то мастер сначала настроит базу данных для Stretch Database. Следуйте указаниям в статье [Запуск мастера включения растяжения для базы данных](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md) вместо пошаговых инструкций в этой статье.  
  
 **Разрешения**. Чтобы настроить Stretch Database для таблицы или базы данных, требуются разрешения db_owner. Чтобы включить Stretch Database в таблице, нужно обладать правами на изменение таблицы.  

 > [!NOTE]
 > В случае последующего отключения Stretch Database для таблицы или базы данных помните, что такое отключение не приводит к удалению дистанционного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены вручную, их хранение будет сопровождаться затратами в Azure.
 
##  <a name="use-the-wizard-to-enable-stretch-database-on-a-table"></a><a name="EnableWizardTable"></a> Настройка Stretch Database для таблицы в с помощью мастера  
 **Запуск мастера**  
 1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу, для которой нужно включить перенос.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Растяжение**и **Включить** , чтобы запустить мастер.  
  
 **Введение**  
 Изучите информацию о назначении мастера и предварительные требования.  
  
 **Выбор таблиц из базы данных**  
 Убедитесь, что выбрана нужная таблица.  
  
 Можно перенести таблицу полностью или указать простую функцию фильтров в мастере. Если вы хотите использовать другой тип функции фильтров, чтобы выбрать строки для переноса, выполните одно из следующих действий.  
  
-   Закройте мастер и выполните инструкцию ALTER TABLE, чтобы включить растяжение для таблицы и указать функцию фильтров.  
  
-   Выполните инструкцию ALTER TABLE, чтобы указать функцию фильтров после выхода из мастера. Необходимые пошаговые инструкции см. в статье [Добавление функции фильтров после запуска мастера](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md#addafterwiz).  
  
 Синтаксис ALTER TABLE описан далее в этой статье.  
  
 **Сводка**  
 Просмотрите введенные значения и выбранные в мастере параметры. Нажмите кнопку **Готово** , чтобы включить растягивание.  
  
 **Результаты**  
 Просмотрите результаты.  
  
##  <a name="use-transact-sql-to-enable-stretch-database-on-a-table"></a><a name="EnableTSQLTable"></a> Настройка Stretch Database для таблицы с помощью Transact-SQL  
 Вы можете включить Stretch Database для существующей таблицы или создать новую таблицу с поддержкой Stretch Database с помощью Transact-SQL.  
  
### <a name="options"></a>Параметры  
 При выполнении CREATE TABLE или ALTER TABLE для включения Stretch Database для таблицы используйте следующие параметры.  
  
-   Если в таблице содержатся горячие и холодные данные, можно использовать предложение `FILTER_PREDICATE = <function>` , чтобы задать функцию для выбора переносимых строк. Этот предикат должен вызывать встроенную функцию с табличным значением. Дополнительные сведения см. в разделе [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md). Если функция фильтров не указана, переносится вся таблица.  
  
    > [!IMPORTANT]  
    > Если указать плохо оптимизированную функцию фильтров, перенос данных будет выполняться медленно. База данных Stretch применяет функцию фильтров к таблице с помощью оператора CROSS APPLY.  
  
-   Укажите `MIGRATION_STATE = OUTBOUND` , чтобы немедленно запустить перенос данных, либо  `MIGRATION_STATE = PAUSED` , чтобы отложить его.  
  
### <a name="enable-stretch-database-for-an-existing-table"></a>Включение Stretch Database для существующей таблицы  
 Чтобы настроить существующую таблицу для использования со службой Stretch Database, выполните инструкцию ALTER TABLE.  
  
 Ниже приведен пример, в котором переносится вся таблица и перенос данных начинается немедленно.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <table name>  
    SET ( REMOTE_DATA_ARCHIVE = ON ( MIGRATION_STATE = OUTBOUND ) ) ;  
GO
```  
  
 Ниже приведен пример, в котором переносятся только строки, возвращаемые встроенной функцией с табличным значением `dbo.fn_stretchpredicate` . Начало переноса откладывается. Дополнительные сведения о функции фильтров см. в статье [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <table name>  
    SET ( REMOTE_DATA_ARCHIVE = ON (  
        FILTER_PREDICATE = dbo.fn_stretchpredicate(),  
        MIGRATION_STATE = PAUSED ) ) ;  
 GO
```  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
### <a name="create-a-new-table-with-stretch-database-enabled"></a>Создание новой таблицы с поддержкой Stretch Database  
 Чтобы создать новую таблицу с поддержкой Stretch Database, выполните команду CREATE TABLE.  
  
 Ниже приведен пример, в котором переносится вся таблица и перенос данных начинается немедленно.  
  
```sql  
USE <Stretch-enabled database name>;
GO
CREATE TABLE <table name>
    ( ... )  
    WITH ( REMOTE_DATA_ARCHIVE = ON ( MIGRATION_STATE = OUTBOUND ) ) ;  
GO
```  
  
 Ниже приведен пример, в котором переносятся только строки, возвращаемые встроенной функцией с табличным значением `dbo.fn_stretchpredicate` . Начало переноса откладывается. Дополнительные сведения о функции фильтров см. в статье [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
```sql  
USE <Stretch-enabled database name>;
GO
CREATE TABLE <table name> 
    ( ... )  
    WITH ( REMOTE_DATA_ARCHIVE = ON (  
        FILTER_PREDICATE = dbo.fn_stretchpredicate(),  
        MIGRATION_STATE = PAUSED ) ) ;  
GO  
```  
  
 Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
  
  
