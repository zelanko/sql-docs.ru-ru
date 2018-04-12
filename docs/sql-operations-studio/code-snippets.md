---
title: Создание фрагментов кода в SQL Operations Studio (preview) | Документы Microsoft
description: Узнайте, как создавать и использовать фрагменты кода SQL в SQL Operations Studio (preview)
ms.custom: tools|sos
ms.date: 11/15/2017
ms.reviewer: alayu; erickang; sstein
ms.prod: sql-non-specified
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4670c824b1e52776c3d81d097beeb4ccd9e62e2d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>Создание и использование фрагментов кода для быстрого создания скриптов Transact-SQL (T-SQL) в[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Фрагменты кода в Code [!INCLUDE[name-sos](../includes/name-sos-short.md)] , шаблоны, которые упрощают создание баз данных и объектов базы данных. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]предоставляет несколько фрагментов кода T-SQL для упрощения быстрого создания правильный синтаксис. 

Можно также создать пользовательские фрагменты.

## <a name="using-built-in-t-sql-code-snippets"></a>С помощью встроенных фрагментов кода T-SQL

1. Чтобы получить доступ к доступные фрагменты кода, введите *sql* в редакторе запросов, чтобы открыть список:

   ![фрагменты кода](media/code-snippets/sql-snippets.png)

1. Выберите фрагмент кода, который вы хотите использовать, и создает скрипт T-SQL. Например, выберите *sqlCreateTable*:

   ![Создание таблицы фрагменты кода](media/code-snippets/create-table.png)

1. Обновите выделенные поля особые значения. Например, замените *TableName* и *схемы* со значениями для своей базы данных:

   ![Замените поле шаблона](media/code-snippets/table-from-snippet.png)

   Если вы хотите изменить поле больше не выделена (это происходит при перемещении курсора вокруг редактора), щелкните правой кнопкой мыши word, вы хотите изменить и выберите пункт **замены всех вхождений**:

   ![Замените поле шаблона](media/code-snippets/change-all.png)

1. Обновить или добавить любые дополнительные T-SQL, необходимые для выбранного фрагмента. Например, обновление *Column1*, *Column2*и добавить дополнительные столбцы.


 
## <a name="creating-sql-code-snippets"></a>Создание фрагментов кода SQL 

Вы можете определить свои собственные фрагменты. Чтобы открыть для редактирования файла фрагмента SQL:

1. Откройте *палитры команд* (**Shift + Ctrl + P**) и тип *фрагмент*и выберите **предпочтения: Откройте фрагменты пользователя**:

   ![Замените поле шаблона](media/code-snippets/user-snippets.png)

1. Выберите **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)]наследует его функциональность фрагмента кода из кода Visual Studio, в частности, в этой статье описывается с помощью фрагментов кода SQL. Дополнительные сведения см. в разделе [Создание собственных фрагментов](https://code.visualstudio.com/docs/editor/userdefinedsnippets) в документации по Visual Studio Code. 

   ![Замените поле шаблона](media/code-snippets/select-sql.png)

1. Вставьте следующий код в *sql.json*:

   ```sql
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   ```

1. Сохраните файл sql.json.
1. Откройте новое окно редактора запросов, нажав кнопку **Ctrl + N**.
2. Тип **sql**, и вы увидите два пользователя фрагменты кода, вы только что добавили; *sqlCreateTable2* и *sqlSelectTop5*.

Выберите один из новых фрагментов и присвойте ему тестового запуска.


## <a name="additional-resources"></a>Дополнительные ресурсы

Сведения о редакторе SQL см. в разделе [учебник редактора кода](tutorial-sql-editor.md).