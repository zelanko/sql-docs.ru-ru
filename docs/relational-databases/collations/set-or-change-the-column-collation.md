---
description: Задание или изменение параметров сортировки столбца
title: Установка и изменение параметров сортировки для столбца | Документация Майкрософт
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 98faafb23e6f5c3f981fdf04eca99a7ab3eb7a7b
ms.sourcegitcommit: 49ee3d388ddb52ed9cf78d42cff7797ad6d668f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94384828"
---
# <a name="set-or-change-the-column-collation"></a>Задание или изменение параметров сортировки столбца
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Для типов данных **char** , **varchar** , **text** , **nchar** , **nvarchar** и **ntext** параметры сортировки базы данных можно переопределить, указав другие параметры сортировки для определенного столбца таблицы одним из следующих способов.  
  
-   Предложение COLLATE в инструкциях [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) и [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md), как указано в примерах ниже. 

    -   **Преобразование на месте.** Рассмотрим одну из существующих таблиц, определенных ниже:

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);

        -- VARCHAR column is encoded the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        ```

        Чтобы преобразовать столбец на месте для использования UTF-8, выполните инструкцию `ALTER COLUMN`, которая задает требуемый тип данных и параметры сортировки с поддержкой UTF-8:

        ```sql 
        ALTER TABLE dbo.MyTable 
        ALTER COLUMN CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8
        ```

        Этот метод прост в реализации, однако эта операция может вызывать блокировку, а это может стать проблемой для больших таблиц и занятых приложений.

    -   **Копирование и замена.** Рассмотрим одну из существующих таблиц, определенных ниже:

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);
        GO

        -- VARCHAR column is encoded using the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        GO
        ```

        Чтобы преобразовать столбец для использования UTF-8, скопируйте данные в новую таблицу, где целевой столбец уже имеет требуемый тип данных и параметры сортировки с поддержкой UTF-8, а затем замените старую таблицу:

        ```sql
        CREATE TABLE dbo.MyTableNew (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8);
        GO
        INSERT INTO dbo.MyTableNew 
        SELECT * FROM dbo.MyTable;
        GO
        DROP TABLE dbo.MyTable;
        GO
        EXEC sp_rename 'dbo.MyTableNew', 'dbo.MyTable';
        GO
        ```

        Этот метод гораздо быстрее, чем преобразование на месте, но обработка сложных схем со множеством зависимостей (внешние ключи, первичные ключи, триггеры, DF) и синхронизация заключительного фрагмента таблицы (если база данных используется) требует больше планирования.
        
    Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Изменение столбцов (ядро СУБД)](../../relational-databases/tables/modify-columns-database-engine.md#SSMSProcedure).  
  
-   Использование свойства **Column.Collation** в объектах SMO [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Невозможно изменить параметры сортировки столбца, на который ссылаются:  
  
-   вычисляемый столбец;  
-   индекс;  
-   статистика распределения, созданная автоматически либо с помощью инструкции `CREATE STATISTICS`;  
-   ограничение CHECK;  
-   ограничение FOREIGN KEY.  
  
 При работе с базой данных **tempdb** предложение [COLLATE](~/t-sql/statements/collations.md) содержит параметр *database_default* , указывающий, что столбец, находящийся во временной таблице, использует параметры сортировки по умолчанию для текущей базы данных пользователя для соединения, а не параметра сортировки базы данных **tempdb**.  
  
## <a name="collations-and-text-columns"></a>Параметры сортировки и столбцы типа text  
 В столбце типа **text** можно добавлять или обновлять значения, имеющие параметры сортировки, отличные от кодовой страницы параметров сортировки по умолчанию для базы данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно преобразует значения в параметры сортировки столбца.  
  
## <a name="collations-and-tempdb"></a>Параметры сортировки и база данных tempdb  
 База данных **tempdb** создается каждый раз при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и имеет те же параметры сортировки по умолчанию, что и база данных **model** . Обычно они совпадают с параметрами сортировки экземпляра. Если при создании пользовательской базы данных указываются параметры сортировки, отличные от параметров сортировки базы данных **model** , то параметры сортировки пользовательской базы данных будут отличаться от базы данных **tempdb**. Все временные хранимые процедуры и временные таблицы создаются и сохраняются в базе данных **tempdb**. Это означает, что неявно столбцы временных таблиц и все константы, переменные и параметры хранимых процедур имеют параметры сортировки, отличные от сравниваемых объектов, создаваемых в постоянных таблицах и хранимых процедурах.  
  
 Это может привести к проблемам из-за различия параметров сортировки у объектов в пользовательских и системных базах данных. Например, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует параметры сортировки Latin1_General_CS_AS, выполняется следующая инструкция:  
  
```sql  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 В рассматриваемой системе база данных **tempdb** использует параметры сортировки Latin1_General_CS_AS с кодовой страницей 1252, а база данных `TestDB` и столбец `TestPermTab.Col1` — параметры сортировки `Estonian_CS_AS` с кодовой страницей 1257. Пример:  
  
```sql  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Согласно предыдущему примеру, база данных **tempdb** использует параметры сортировки Latin1_General_CS_AS, а база данных `TestDB` и столбец `TestTab.Col1` параметры сортировки `Estonian_CS_AS` . Пример:  
  
```sql  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Поскольку база данных **tempdb** использует параметры сортировки сервера по умолчанию, а `TestPermTab.Col1` — другие параметры сортировки, SQL Server возвратит следующую ошибку: "Не удалось разрешить конфликт параметров сортировки между "Latin1_General_CI_AS_KS_WS" и "Estonian_CS_AS" в операции равенства".  
  
 Избавиться от этой ошибки можно одним из следующих способов:  
  
-   укажите, что столбец временной таблицы использует параметры сортировки по умолчанию пользовательской базы данных, а не базы данных **tempdb**. Это позволит таблице работать с аналогичными таблицами в разных базах данных, если это необходимо;  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   укажите правильные параметры сортировки в столбце `#TestTempTab` :  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>См. также  
 [Задание или изменение параметров сортировки сервера](../../relational-databases/collations/set-or-change-the-server-collation.md)   
 [Установка и изменение параметров сортировки базы данных](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
