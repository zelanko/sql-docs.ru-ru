---
title: Создание многократно используемых фрагментов кода
titleSuffix: Azure Data Studio
description: Узнайте, как создать и использовать фрагменты кода SQL в Azure Data Studio.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 09a8432d10a70bb8530654d76bce874f735788a6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67959703"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>создание и использование фрагментов кода для быстрого создания скриптов Transact-SQL (T-SQL) в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Фрагменты кода в [!INCLUDE[name-sos](../includes/name-sos-short.md)] — это шаблоны, которые упрощают создание баз данных и объектов базы данных. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] предоставляет несколько фрагментов T-SQL, которые помогают быстро создавать правильные синтаксические конструкции. 

Кроме того, можно создавать пользовательские фрагменты кода.

## <a name="using-built-in-t-sql-code-snippets"></a>Использование встроенных фрагментов кода T-SQL

1. Для доступа к имеющимся фрагментам введите *sql* в редакторе запросов, чтобы открыть список:

   ![фрагменты кода](media/code-snippets/sql-snippets.png)

1. Выберите нужный фрагмент, и на его основе будет создан скрипт T-SQL. Например, выберите *sqlCreateTable*:

   ![фрагменты для создания таблиц](media/code-snippets/create-table.png)

1. Замените значения выделенных полей на собственные. Например, замените значения *TableName* и *Schema* на значения для вашей базы данных:

   ![замена поля шаблона](media/code-snippets/table-from-snippet.png)

   Если поле, которое нужно изменить, больше не выделено (это происходит при перемещении курсора по редактору), щелкните правой кнопкой мыши слово, которое нужно заменить, и выберите команду **Изменить все вхождения**:

   ![замена поля шаблона](media/code-snippets/change-all.png)

1. Измените или добавьте дополнительные элементы T-SQL для выбранного фрагмента. Например, измените столбцы *Column1* и *Column2* и добавьте дополнительные столбцы.


 
## <a name="creating-sql-code-snippets"></a>Создание фрагментов кода SQL 

Вы можете определять собственные фрагменты. Чтобы открыть файл фрагмента SQL для редактирования, выполните указанные ниже действия.

1. Откройте *палитру команд* (**SHIFT+CTRL+P**), введите *snip* и выберите **Настройки: открыть пользовательские фрагменты**:

   ![замена поля шаблона](media/code-snippets/user-snippets.png)

1. Выберите **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует функциональные возможности фрагментов кода от Visual Studio Code, поэтому в этой статье рассматривается использование фрагментов SQL. Более подробные сведения см. в статье [Создание собственных фрагментов](https://code.visualstudio.com/docs/editor/userdefinedsnippets) в документации по Visual Studio Code. 

   ![замена поля шаблона](media/code-snippets/select-sql.png)

1. Вставьте следующий код в файл *sql.json*:

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
1. Откройте новое окно редактора запросов, нажав клавиши **CTRL+N**.
2. Введите **sql**, и вы увидите два только что добавленных пользовательских фрагмента: *sqlCreateTable2* и *sqlSelectTop5*.

Выберите один из новых фрагментов и выполните его тестовый запуск.


## <a name="additional-resources"></a>Дополнительные ресурсы

Сведения о редакторе SQL см. в [учебнике по редактору кода](tutorial-sql-editor.md).
