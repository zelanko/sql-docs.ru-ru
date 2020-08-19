---
description: Учебник по T-SQL. Создание объектов базы данных и запросов к ним
title: Учебник T-SQL. Создание объектов базы данных и отправка запросов к ним | Документация Майкрософт
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a489da04d7a65bf854cebf06e8103e22c1abc12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459180"
---
# <a name="lesson-1-create-and-query-database-objects"></a>Урок 1. Создание объектов базы данных и отправка запросов к ним
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

На этом занятии вы узнаете, как создать базу данных, создать таблицу в базе данных и получить доступ к данным таблицы и изменить их. Поскольку это занятие является введением к использованию языка [!INCLUDE[tsql](../includes/tsql-md.md)], в нем не используются и не описываются многие параметры, доступные для этих инструкций.  
  
[!INCLUDE[tsql](../includes/tsql-md.md)] могут быть написаны и пересланы компоненту [!INCLUDE[ssDE](../includes/ssde-md.md)] следующими способами:  
  
-   При помощи среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Предполагается, что вы используете среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], но можно также использовать среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, которая может быть загружена бесплатно с веб-узла [центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=14630).  
  
-   Посредством программы [sqlcmd](../tools/sqlcmd-utility.md).  
  
-   Соединившись из создаваемого приложения.  
  
Исходный код исполняется в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)] таким же образом и с теми же разрешениями, независимо от того, как был передан исходный код инструкций.  
  
Чтобы выполнить инструкцию языка [!INCLUDE[tsql](../includes/tsql-md.md)] в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], откройте среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и соединитесь с экземпляром компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].  

## <a name="prerequisites"></a>Предварительные требования
Для работы с этим руководством необходима среда SQL Server Management Studio и доступ к экземпляру SQL Server. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Если у вас нет экземпляра SQL Server, создайте его. Чтобы создать экземпляр, выберите свою платформу по следующим ссылкам. При выборе проверки подлинности SQL используйте учетные данные SQL Server.
- **Windows**: [скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- **macOS**: [скачать SQL Server 2017 для Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker).

## <a name="create-a-database"></a>Создание базы данных
Как и у многих инструкций языка [!INCLUDE[tsql](../includes/tsql-md.md)], у инструкции [`CREATE DATABASE`](statements/create-database-transact-sql.md) имеется обязательный параметр: имя базы данных.` CREATE DATABASE` Кроме этого, у инструкции имеется ряд необязательных параметров, таких как расположение на диске, где требуется хранить файлы базы данных. При выполнении инструкции `CREATE DATABASE` без дополнительных параметров для многих из них [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует значения по умолчанию.

1.  В окне редактора запросов введите, но не выполняйте, следующий код:  
  
    ```sql  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  С помощью указателя выделите слова `CREATE DATABASE`и нажмите клавишу **F1**. Должен открыться раздел `CREATE DATABASE` электронной документации на Microsoft SQL Server. Таким же способом можно найти полный синтаксис инструкции `CREATE DATABASE` и других инструкций, используемых в данном учебнике.  
  
3.  В редакторе запросов нажмите клавишу **F5** , чтобы выполнить инструкцию и создать базу данных с именем `TestData`.  
  
При создании базы данных сервер [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает копию базы данных **model** и присваивает ей указанное имя базы данных. Эта операция обычно занимает несколько секунд, если только с помощью дополнительного параметра не указан большой исходный размер базы данных.  
  
> [!NOTE]  
> Когда в одном пакете представлено несколько инструкций, они разделяются с помощью ключевого слова GO. Ключевое слово GO является необязательным, если в пакете содержится только одна инструкция.  

## <a name="create-a-table"></a>Создание таблицы

[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Чтобы создать таблицу, нужно указать имя таблицы, имена и типы данных для каждого столбца таблицы. Также рекомендуется указывать, допускаются ли значения NULL для каждого из столбцов. Для создания таблицы необходимо иметь разрешение `CREATE TABLE` и разрешение `ALTER SCHEMA` для схемы, которая будет содержать таблицу. Предопределенная роль базы данных [`db_ddladmin`](../relational-databases/security/authentication-access/database-level-roles.md) имеет эти разрешения.  
  
Большинство таблиц имеют первичный ключ, состоящий из одной или нескольких столбцов таблицы. Первичный ключ всегда уникален. Компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] потребует выполнения условия неповторения значения первичного ключа в таблице.  
  
Список типов данных и ссылки на их описание см. в разделе [Типы данных (Transact-SQL)](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> Компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] может быть установлен с учетом регистра и без учета регистра. Если компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] установлен с учетом регистра, имена объектов должны иметь одно и тоже имя. Например, таблица с именем OrderData будет отличаться от таблицы ORDERDATA. Если компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] установлен без учета регистра, эти два имени таблицы будут рассматриваться как одна таблица, то есть имя может быть использовано только один раз.  
  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a>Переключение соединения редактора запросов на базу данных TestData  

В окне редактора запросов введите и выполните следующий код, чтобы изменить соединение на базу данных `TestData` .  
  
  ```sql  
  USE TestData  
  GO  
  ```  
  
### <a name="create-the-table"></a>Создание таблицы

В окне редактора запросов введите и выполните следующий код, чтобы создать таблицу `Products`. Столбцы таблицы имеют имена `ProductID`, `ProductName`, `Price`и `ProductDescription`. Столбец `ProductID` является первичным ключом таблицы. `int`, `varchar(25)`, `money`и `varchar(max)` . Только столбцы `Price` и `ProductionDescription` могут быть пустыми при вставке или изменении строки. Данная инструкция содержит необязательный элемент (`dbo.`), называемый схемой. Схема — это объект базы данных, к которому принадлежит таблица. Если вы являетесь администратором, схемой по умолчанию будет схема `dbo` . `dbo` означает владельца базы данных.  
  
  ```sql  
  CREATE TABLE dbo.Products  
     (ProductID int PRIMARY KEY NOT NULL,  
     ProductName varchar(25) NOT NULL,  
     Price money NULL,  
     ProductDescription varchar(max) NULL)  
  GO  
 ```  

## <a name="insert-and-update-data-in-a-table"></a>Вставка данных в таблицу и их обновление
 После создания таблицы **Products** в нее можно вставлять данные с помощью инструкции INSERT. После вставки данных содержимое строки изменяется с помощью инструкции UPDATE. Предложение WHERE предназначено для ограничения числа строк, изменяемых в процессе выполнения инструкции UPDATE до одной строки. Чтобы ввести следующие данные, потребуется четыре инструкции.  
  
|ProductID|ProductName|Цена|ProductDescription|  
|-------------|---------------|---------|----------------------|  
|1|Clamp|12,48|Workbench clamp|  
|50|Screwdriver|3,17|Flat head|  
|75|Tire Bar||Tool for changing tires.|  
|3000|3 mm Bracket|0,52||  
  
Базовый синтаксис: INSERT, имя таблицы, список столбцов, VALUES, а затем список добавляемых значений. Два дефиса в начале строки означают, что строка является примечанием и текст не будет обрабатываться компилятором. В этом случае примечание описывает возможные варианты синтаксиса.  
  
### <a name="insert-data-into-a-table"></a>Вставка данных в таблицу  
  
1.  Выполните следующую инструкцию, чтобы добавить строку в таблицу `Products` , которая была создана в предыдущей задаче.
  
   ```sql 
   -- Standard syntax  
   INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
       VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
   GO   
   ```  

   > [!NOTE]
   > Если вставка выполнена, перейдите к следующему шагу.
   >
   > Если вставка завершается сбоем, это может быть вызвано тем, что в таблице `Product` уже есть строка с таким ИД продукта. Чтобы продолжить, удалите все строки в таблице и повторите предыдущий шаг. [`TRUNCATE TABLE`](statements/truncate-table-transact-sql.md) удаляет все строки в таблице. 
   >
   > Выполните следующую команду, чтобы удалить все строки в таблице:
   > 
   > ```sql
   >TRUNCATE TABLE TestData.dbo.Products;
   > GO
   >```
   >
   > После усечения таблицы повторите команду `INSERT` на этом шаге.

2.  В следующей инструкции показано, как можно изменить порядок, в котором приведены параметры, изменив расположение `ProductID` и `ProductName` одновременно как в списке полей (в круглых скобках), так и в списке значений.  
  
   ```sql  
   -- Changing the order of the columns  
   INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
       VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
   GO    
   ```  
  
3.  Следующая инструкция показывает, что имена столбцов перечислять не обязательно, если значения перечислены в нужном порядке. Этот синтаксис является стандартным, но не рекомендуется, поскольку другим будет трудно понять ваш код. `NULL` указано в столбце `Price` , так как цена этого товара пока неизвестна.  
  
   ```sql  
   -- Skipping the column list, but keeping the values in order  
   INSERT dbo.Products  
       VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
   GO  
  ```  
  
4.  Имя схемы указывать не обязательно, пока доступ и изменение таблицы осуществляются с помощью схемы по умолчанию. Поскольку в столбце `ProductDescription` разрешены значения NULL и значение для столбца не приведено, имя и значение столбца `ProductDescription` в инструкции могут быть полностью опущены.  
  
   ```sql  
   -- Dropping the optional dbo and dropping the ProductDescription column  
   INSERT Products (ProductID, ProductName, Price)  
       VALUES (3000, '3 mm Bracket', 0.52)  
   GO  
   ```  
  
### <a name="update-the-products-table"></a>Обновление таблицы продуктов  
Введите и выполните следующую инструкцию `UPDATE` , чтобы изменить значение `ProductName` второго продукта со значения `Screwdriver`на значение `Flat Head Screwdriver`.  
  
  ```sql  
  UPDATE dbo.Products  
      SET ProductName = 'Flat Head Screwdriver'  
      WHERE ProductID = 50  
  GO  
  ```  

## <a name="read-data-from-a-table"></a>Чтение данных из таблицы
Для чтения данных в таблице используется инструкция SELECT. Инструкция SELECT является одной из наиболее важных инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] , и для нее существует много разновидностей синтаксиса. В этом учебнике будет показана работа с пятью простыми вариантами.  
  
### <a name="read-the-data-in-a-table"></a>Чтение данных в таблице  
  
1.  Чтобы прочитать данные из таблицы `Products` , введите и выполните следующие инструкции.  
  
  ```sql 
  -- The basic syntax for reading data from a single table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
  GO  
  ```  
  
2.  Чтобы выбрать все столбцы в таблице, можно использовать звездочку (`*`). Звездочка используется для нерегламентированных запросов. В постоянном коде укажите список всех столбцов, чтобы инструкция возвращала нужные столбцы, даже если какой-то столбец будет добавлен в таблицу позднее.  
  
  ```sql  
  -- Returns all columns in the table  
  -- Does not use the optional schema, dbo  
  SELECT * FROM Products  
  GO   
  ```  
  
3.  Если нет необходимости возвращать определенные столбцы, их можно опустить. Столбцы возвращаются в том порядке, в котором они перечислены.  
  
  ```sql  
  -- Returns only two of the columns from the table  
  SELECT ProductName, Price  
      FROM dbo.Products  
  GO    
  ```  
  
4.  Чтобы ограничить количество строк, возвращаемых пользователю, используйте предложение `WHERE` .  
  
  ``` sql 
  -- Returns only two of the records in the table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
      WHERE ProductID < 60  
  GO    
  ```  
  
5.  Можно работать со значениями столбцов, по мере того как столбцы возвращаются. В следующем примере выполняется математическая операция над столбцом `Price` . Столбцы, изменяемые подобным образом, не имеют имени, если только имя не указывается с использованием ключевого слова `AS` .  
  
  ```sql  
  -- Returns ProductName and the Price including a 7% tax  
  -- Provides the name CustomerPays for the calculated column  
  SELECT ProductName, Price * 1.07 AS CustomerPays  
      FROM dbo.Products  
  GO  
  ```  
  
### <a name="useful-functions-in-a-select-statement"></a>Полезные функции в инструкции SELECT  
Сведения о работе с функциями, которые используются в инструкциях SELECT, см. в следующих разделах:  

:::row:::
    :::column:::
        [Строковые функции (Transact-SQL)](../t-sql/functions/string-functions-transact-sql.md)
    :::column-end:::
    :::column:::
        [Типы данных и функции даты и времени (Transact-SQL)](../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [Математические функции (Transact-SQL)](../t-sql/functions/mathematical-functions-transact-sql.md)
    :::column-end:::
    :::column:::
        [Функции для работы с изображениями и текстом (Transact-SQL)](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)
    :::column-end:::
:::row-end:::

## <a name="create-views-and-stored-procedures"></a>Создание представлений и хранимых процедур
Представление является хранимой инструкцией SELECT, а хранимая процедура представляет собой одну или более инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] , выполняемых в виде пакета.  
  
Представления запрашиваются так же, как таблицы, и не принимают параметры. Хранимые процедуры сложнее, чем представления. Хранимые процедуры содержат как входные, так и выходные параметры и могут содержать инструкции, которые управляют потоком кода, например IF и WHILE. Использование хранимых процедур для всех повторяющихся действий в базе данных является хорошим стилем программирования.  
  
В этом примере используется инструкция CREATE VIEW, чтобы создать представление, которое выбирает только два столбца в таблице **Products** . Затем с помощью инструкции CREATE PROCEDURE создается хранимая процедура, которая принимает цену в качестве параметра и возвращает только те продукты, цена которых меньше значения, указанного в качестве параметра.  
  
### <a name="create-a-view"></a>Создание представления  
  
Выполните следующую инструкцию, создающую представление, которое выполняет инструкцию select и возвращает названия и цены продуктов пользователю.  
  
  ```sql  
  CREATE VIEW vw_Names  
     AS  
     SELECT ProductName, Price FROM Products;  
  GO    
  ```  
  
### <a name="test-the-view"></a>Тестирование представления  
  
С представлениями обращаются так же, как с таблицами. Используйте инструкцию `SELECT` , чтобы получить доступ к представлению.  
  
  ```sql  
  SELECT * FROM vw_Names;  
  GO   
  ```  
  
### <a name="create-a-stored-procedure"></a>Создание хранимой процедуры  
  
В следующем примере создается хранимая процедура `pr_Names`с входным параметром `@VarPrice` типа `money`. Эта хранимая процедура печатает инструкцию `Products less than` , соединенную операцией сцепления с входным параметром, тип которого преобразуется из `money` в `varchar(10)` . Затем процедура выполняет инструкцию `SELECT` на представлении, передавая входной параметр в предложение `WHERE` . Возвращаются все продукты, цена которых меньше значения входного параметра.  
  
  ```sql  
  CREATE PROCEDURE pr_Names @VarPrice money  
     AS  
     BEGIN  
        -- The print statement returns text to the user  
        PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
        -- A second statement starts here  
        SELECT ProductName, Price FROM vw_Names  
              WHERE Price < @varPrice;  
     END  
  GO    
  ```  
  
### <a name="test-the-stored-procedure"></a>Тестирование хранимой процедуры  
  
Чтобы выполнить хранимую процедуру, введите и выполните следующую инструкцию. Эта процедура должна возвратить названия двух продуктов, введенных в таблицу `Products` на занятии 1, цена которых меньше `10.00`.  
  
  ```sql  
  EXECUTE pr_Names 10.00;  
  GO  
  ```  

## <a name="next-steps"></a>Дальнейшие действия
В следующей статье вы узнаете, как настроить разрешения в объектах базы данных. Объекты, созданные в уроке 1, также будут использоваться в уроке 2. 

Дополнительные сведения см. в следующей статье:
> [!div class="nextstepaction"]
> [Следующие шаги](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)
  
  
  
