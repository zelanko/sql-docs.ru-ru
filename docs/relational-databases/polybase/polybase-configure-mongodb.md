---
title: 'Доступ к внешним данным: MongoDB — PolyBase'
description: В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в MongoDB. Создание внешних таблиц для ссылки на внешние данные.
ms.date: 12/13/2019
ms.metadata: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15'
ms.openlocfilehash: fdbc2112467cadc2aaec390a667e3d189786b3ef
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467495"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>Настройка PolyBase для доступа к внешним данным в MongoDB

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в MongoDB.

## <a name="prerequisites"></a>Предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md).

[Главный ключ](../../t-sql/statements/create-master-key-transact-sql.md) необходимо создать перед созданием учетных данных для базы данных. 
    

## <a name="configure-a-mongodb-external-data-source"></a>Настройка внешнего источника данных MongoDB

Чтобы запросить данные из источника данных MongoDB, необходимо создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц.

В рамках этого раздела используются следующие команды Transact-SQL:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Создайте учетные данные в области базы данных для доступа к источнику MongoDB.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```
    
   > [!IMPORTANT] 
   > Соединитель ODBC MongoDB для PolyBase поддерживает только обычную проверку подлинности, но не проверку подлинности Kerberos.    
    
1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH (LOCATION = 'mongodb://<server>[:<port>]',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_name);
    ```

1. **Необязательно**. Создайте статистику внешней таблицы.

    Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>После создания внешнего источника данных можно использовать команду [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md), чтобы создать таблицу с поддержкой запросов по этому источнику.
>
>Пример см. в разделе [Создание внешней таблицы для MongoDB](../../t-sql/statements/create-external-table-transact-sql.md#k-create-an-external-table-for-mongodb).

## <a name="flattening"></a>Преобразование в плоскую структуру
Преобразование в плоскую структуру доступно для вложенных и повторяющихся данных из коллекций документов MongoDB. Пользователь должен включить функцию `create an external table` и явным образом указать реляционную схему для коллекций документов MongoDB, которые могут содержать вложенные и повторяющиеся данные. Вложенные или повторяющиеся типы данных JSON будут преобразованы в плоскую структуру следующим образом.

* Объект: коллекция неупорядоченных ключей и значений, заключенная в фигурные скобки (вложенные данные)

   - SQL Server создаст столбец таблицы для каждого ключа объекта.

     * Имя столбца: objectname_keyname

* Массив: упорядоченные значения, разделенные запятыми и заключенные в квадратные скобки (повторяющиеся данные)

   - SQL Server добавит новую строку таблицы для каждого элемента массива.

   - SQL Server создаст столбец для каждого массива, чтобы хранить индекс элементов массива.

     * Имя столбца: arrayname_index

     * Тип данных: bigint

Использование этого метода может привести к возникновению ряда проблем. Далее указаны две из них:

* пустое повторяющееся поле будет маскировать данные, содержащиеся в плоских полях в той же записи;

* наличие нескольких повторяющихся полей может привести к резкому увеличению количества создаваемых строк.

Например, SQL Server оценивает образец коллекции с набором данных по ресторанам MongoDB, сохраненный в нереляционном формате JSON. У каждого ресторана есть вложенное поле адреса и массив оценок, которые он получил в разные дни. На рисунке ниже показан стандартный ресторан с вложенным адресом и вложенными повторяющимися оценками.

![Преобразование данных MongoDB в плоскую структуру](../../relational-databases/polybase/media/mongo-flattening.png "Преобразование данных MongoDB о ресторане в плоскую структуру")

Адрес объекта будет преобразован в плоскую структуру, как показано ниже:

* вложенное поле restaurant.address.building преобразуется в restaurant.address_building;
* вложенное поле restaurant.address.coord преобразуется в restaurant.address_coord;
* вложенное поле restaurant.address.street преобразуется в restaurant.address_street;
* вложенное поле restaurant.address.zipcode преобразуется в restaurant.address_zipcode.

Массив оценок будет преобразован в плоскую структуру, как показано ниже:

| grades_date | grades_grade  | games_score | 
| ------------- | ------------------------- | -------------- |
|1393804800000 |Объект |2|
|1378857600000|Объект |6|
|135898560000 |Объект |10|
|1322006400000|Объект |9|
|1299715200000 |B |14|

## <a name="cosmos-db-connection"></a>Подключение Cosmos DB

Используя API Mongo в Cosmos DB и соединитель Mongo DB PolyBase, вы можете создать внешнюю таблицу **экземпляра Cosmos DB**. Для этого выполните те же действия, что указаны выше. Учетные данные в области базы данных, а также адрес сервера, порт и строка расположения должны соответствовать серверу Cosmos DB. 

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
