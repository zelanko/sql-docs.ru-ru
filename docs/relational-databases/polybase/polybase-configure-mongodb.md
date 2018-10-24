---
title: Настройка PolyBase для доступа к внешним данным в MongoDB | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: a51842a1682b5e02db4ea216bddefbabbf0a7f56
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874312"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>Настройка PolyBase для доступа к внешним данным в MongoDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в MongoDB.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных MongoDB, необходимо создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц.

Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

В этом разделе будут созданы такие объекты:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)
- CREATE EXTERNAL DATA SOURCE (Transact-SQL)
- CREATE EXTERNAL TABLE (Transact-SQL)
- CREATE STATISTICS (Transact-SQL)

1.    Создайте главный ключ в базе данных. Это необходимо для шифрования секрета учетных данных.

      ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
      ```

1.   Создайте учетные данные на уровне базы данных.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL MongoDBCredentials 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1.  Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Укажите расположение внешнего источника данных и учетные данные для источника данных MongoDB.

     ```sql
     /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE MongoInstance
    WITH (
    LOCATION = mongodb://MongoServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = MongoDBCredentials
    );
     ```

1. Создайте схемы для внешних данных.

     ```sql
     CREATE SCHEMA MongoDB;
     GO
     ```

1.  Создайте внешние таблицы, которые представляют данные, хранящиеся во внешней системе MongoDB, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

     ```sql
     /*  LOCATION: MongoDB table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE MongoDB.orders(
     [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
     LOCATION='TPCH..ORDERS',
     DATA_SOURCE= MongoDBInstance
     );
     ```

1. Создайте статистику по внешней таблице для оптимизации производительности.

     ```sql
      CREATE STATISTICS OrdersOrderKeyStatistics ON MongoDB.orders(O_ORDERKEY) WITH FULLSCAN;
     ```

## <a name="flattening"></a>Преобразование в плоскую структуру
 Преобразование в плоскую структуру включено для вложенных и повторяющихся данных из коллекций документов MongoDB. Пользователь должен включить функцию создания внешней таблицы и явным образом указать реляционную схему для коллекций документов MongoDB, которые могут содержать вложенные и (или) повторяющиеся данные. В будущем мы включим возможность автоматического обнаружения схемы в коллекциях документов Mongo.
Вложенные или повторяющиеся типы данных JSON будут преобразованы в плоскую структуру следующим образом.

* Объект: коллекция неупорядоченных ключей и значений, заключенная в фигурные скобки (вложенные данные)

   - Мы создадим столбец таблицы для каждого ключа объекта.

     * Имя столбца: objectname_keyname

* Массив: упорядоченные значения, разделенные запятыми и заключенные в квадратные скобки (повторяющиеся данные)

   - Мы добавим новую строку таблицы для каждого элемента массива.

   - Мы создадим столбец для каждого массива для хранения индекса элемента массива.

     * Имя столбца: arrayname_index

     * Тип данных: bigint

Использование этого метода может привести к возникновению ряда проблем. Далее указаны две из них:

* пустое повторяющееся поле будет маскировать данные, содержащиеся в плоских полях в той же записи;

* наличие нескольких повторяющихся полей может привести к резкому увеличению количества создаваемых строк.

В качестве примера оценим образец коллекции с набором данных по ресторанам MongoDB, сохраненный в нереляционном формате JSON. У каждого ресторана есть вложенное поле адреса и массив оценок, которые он получил в разные дни. На рисунке ниже показан стандартный ресторан с вложенным адресом и вложенными повторяющимися оценками.

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

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
