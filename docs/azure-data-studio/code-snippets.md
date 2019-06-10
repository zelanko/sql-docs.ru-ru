---
title: Создание фрагментов кода для повторного использования
titleSuffix: Azure Data Studio
description: Узнайте, как создать и использовать фрагменты кода SQL в Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 627608797eb287f9fcf36d8a00df3da1fc8eff75
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803835"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>Создание и использование фрагментов кода для быстрого создания скриптов Transact-SQL (T-SQL) в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Фрагменты кода в [!INCLUDE[name-sos](../includes/name-sos-short.md)] , шаблоны, которые упрощают создание баз данных и объектов базы данных. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] предоставляет несколько фрагментов кода T-SQL для упрощения быстрого создания правильного синтаксиса. 

Также можно создать фрагменты кода, определяемые пользователем.

## <a name="using-built-in-t-sql-code-snippets"></a>С помощью встроенных фрагментов кода T-SQL

1. Чтобы получить доступ к доступные фрагменты кода, введите *sql* в редакторе запросов, чтобы открыть список:

   ![фрагменты кода](media/code-snippets/sql-snippets.png)

1. Выберите фрагмент, который вы хотите использовать, и оно формирует сценарий T-SQL. Например, выберите *sqlCreateTable*:

   ![Создание таблицы фрагментов](media/code-snippets/create-table.png)

1. Обновите выделенными полями с соответствующими значениями. Например, замените *TableName* и *схемы* со значениями для своей базы данных:

   ![Поменяйте местами поля шаблона](media/code-snippets/table-from-snippet.png)

   Если вы хотите изменить поле больше не будет выделен (это происходит при перемещении курсора вокруг редакторе), щелкните правой кнопкой мыши слово, вы хотите изменить и выберите пункт **замените все вхождения**:

   ![Поменяйте местами поля шаблона](media/code-snippets/change-all.png)

1. Обновить или добавить любые дополнительные T-SQL, необходимые для выбранного фрагмента. Например, обновить *Column1*, *Column2*и добавить дополнительные столбцы.


 
## <a name="creating-sql-code-snippets"></a>Создание фрагментов кода SQL 

Вы можете определить собственные фрагменты кода. Чтобы открыть файл фрагмент кода SQL для редактирования:

1. Откройте *палитру команд* (**Shift + Ctrl + P**) и тип *фрагмент*и выберите **предпочтения: Фрагменты пользователя Open**:

   ![Поменяйте местами поля шаблона](media/code-snippets/user-snippets.png)

1. Выберите **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует его функциональность фрагмента кода из Visual Studio Code, поэтому в этой статье специально рассматривается использование фрагментов кода SQL. Дополнительные сведения см. в разделе [Создание собственных фрагментов](https://code.visualstudio.com/docs/editor/userdefinedsnippets) в документации по Visual Studio Code. 

   ![Поменяйте местами поля шаблона](media/code-snippets/select-sql.png)

1. Вставьте следующий код в *sql.json*:

   ```sql
   {
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
   }
   ```

1. Сохраните файл sql.json.
1. Откройте новое окно редактора запросов, щелкнув **Ctrl + N**.
2. Тип **sql**, и вы увидите два пользователя фрагменты, вы только что добавили; *sqlCreateTable2* и *sqlSelectTop5*.

Выберите один из новых фрагментов и присвойте ему тестового запуска.


## <a name="additional-resources"></a>Дополнительные ресурсы

Сведения о редакторе SQL, см. в разделе [учебник редактора кода](tutorial-sql-editor.md).
