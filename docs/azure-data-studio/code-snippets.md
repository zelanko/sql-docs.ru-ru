---
title: Создание многократно используемых фрагментов кода
description: Узнайте, как создавать и использовать фрагменты кода SQL в Azure Data Studio, чтобы упростить создание баз данных и объектов баз данных.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: aa1826539a6b9d2a5f649159e566d3ceda8d624d
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364131"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-azure-data-studio"></a>Создание и использование фрагментов кода для быстрого создания скриптов Transact-SQL (T-SQL) в Azure Data Studio

Фрагменты кода в Azure Data Studio — это шаблоны, которые упрощают создание баз данных и объектов базы данных. 

Azure Data Studio предоставляет несколько фрагментов T-SQL, которые помогают быстро создавать правильные синтаксические конструкции. 

Кроме того, можно создавать пользовательские фрагменты кода.

## <a name="using-built-in-t-sql-code-snippets"></a>Использование встроенных фрагментов кода T-SQL

1. Для доступа к имеющимся фрагментам введите *sql* в редакторе запросов, чтобы открыть список:

   ![фрагменты кода](media/code-snippets/sql-snippets.png)

2. Выберите нужный фрагмент, и на его основе будет создан скрипт T-SQL. Например, выберите *sqlCreateTable*:

   ![фрагменты для создания таблиц](media/code-snippets/create-table.png)

3. Замените значения выделенных полей на собственные. Например, замените значения *TableName* и *Schema* на значения для вашей базы данных:

   ![Таблица из фрагмента](media/code-snippets/table-from-snippet.png)

   Если поле, которое нужно изменить, больше не выделено (это происходит при перемещении курсора по редактору), щелкните правой кнопкой мыши слово, которое нужно заменить, и выберите команду **Изменить все вхождения**:

   ![Изменить все](media/code-snippets/change-all.png)

4. Измените или добавьте дополнительные элементы T-SQL для выбранного фрагмента. Например, измените столбцы *Column1* и *Column2* и добавьте дополнительные столбцы.

## <a name="creating-sql-code-snippets"></a>Создание фрагментов кода SQL

Вы можете определять собственные фрагменты. Чтобы открыть файл фрагмента SQL для редактирования, выполните указанные ниже действия.

1. Откройте *палитру команд* (**SHIFT+CTRL+P**), введите *snip* и выберите **Настройки: открыть пользовательские фрагменты**:

   ![Пользовательские фрагменты](media/code-snippets/user-snippets.png)

2. Выберите **SQL**:

   > [!NOTE]
   > Azure Data Studio наследует функциональные возможности фрагментов кода от Visual Studio Code, поэтому в этой статье рассматривается использование фрагментов SQL. Более подробные сведения см. в статье [Создание собственных фрагментов](https://code.visualstudio.com/docs/editor/userdefinedsnippets) в документации по Visual Studio Code. 

   ![Выбор SQL](media/code-snippets/select-sql.png)

3. Вставьте следующий код в файл *sql.json*:

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
    "$1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "Column1 [NVARCHAR](50) NOT NULL,",
    "Column2 [NVARCHAR](50) NOT NULL",
    "-- specify more columns here",
    ");",
    "GO"
    ],
       "description": "User-defined snippet example 2"
       }
       }
       ```

4. Save the sql.json file.

5. Open a new query editor window by clicking **Ctrl+N**.

6. Type **sql**, and you see the two user snippets you just added; *sqlCreateTable2* and *sqlSelectTop5*.

Select one of the new snippets and give it a test run!

## Next steps

For information about the SQL editor, see [Code editor tutorial](tutorial-sql-editor.md).
