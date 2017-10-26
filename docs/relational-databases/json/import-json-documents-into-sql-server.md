---
title: "Импорт документов JSON на SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e908ec0-7173-4cd2-8f48-2700757b53a5
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 95489b4e72f1321f7e1139f06040eb81a5956b15
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="import-json-documents-into-sql-server"></a>Импорт документов JSON на SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Здесь описывается импорт файлов JSON на SQL Server. Сейчас многие документы JSON хранятся в файлах. Приложения записывают сведения в файлы JSON, в файлах JSON хранятся сведения, созданные датчиками, и т. д. Важно иметь возможность считывать данные JSON, хранящиеся в файлах, загружать эти данные на SQL Server и анализировать их.

## <a name="import-a-json-document-into-a-single-column"></a>Импорт документа JSON в единый столбец
**OPENROWSET(BULK)** представляет собой функцию с табличным значением, с помощью которой можно считывать данные из любого файла на локальном диске или в локальной сети при условии, что у SQL Server есть доступ на чтение в этом расположении. Эта функция возвращает таблицу с одним столбцом, включающим содержимое файла. Функцию OPENROWSET(BULK) можно использовать с различными параметрами, например с разделителями. В самом простом случае вы можете просто загрузить все содержимое файла как текстовое значение. (Это единое большое значение известно как единый большой символьный объект или SINGLE_CLOB.) 

Ниже приведен пример функции **OPENROWSET(BULK)**, с помощью которой содержимое файла JSON сначала считывается, а затем возвращается к пользователю в виде отдельного значения.

```sql
SELECT BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
```

OPENJSON(BULK) считывает содержимое файла и возвращает его в `BulkColumn`.

Вы также можете загрузить содержимое файла в локальную переменную или таблицу, как показано в следующем примере.

```sql
-- Load file contents into a variable
SELECT @json = BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j

-- Load file contents into a table 
SELECT BulkColumn
 INTO #temp 
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
```

После загрузки содержимого JSON-файла текст JSON можно сохранить в таблицу.

## <a name="import-multiple-json-documents"></a>Импорт нескольких документов JSON
Таким же образом можно одновременно загрузить сразу несколько JSON-файлов из файловой системы в локальные переменные. Предположим, у вас есть файлы с именем `book<index>.json`.
  
```sql
DECLARE @i INT = 1
DECLARE @json AS NVARCHAR(MAX)

WHILE(@i < 10)
BEGIN
    SET @file = 'C:\JSON\Books\book' + cast(@i AS VARCHAR(5)) + '.json';
    SELECT @json = BulkColumn FROM OPENROWSET (BULK (@file), SINGLE_CLOB) AS j
    SELECT * FROM OPENJSON(@json) AS json
    -- Optionally, save the JSON text in a table.
    SET @i = @i + 1 ;
END
```

## <a name="import-json-documents-from-azure-file-storage"></a>Импорт документов JSON из хранилища файлов Azure
Используя функцию OPENROWSET(BULK) описанным выше образом, можно также прочитать JSON-файлы из других расположений файлов, к которым у SQL Server есть доступ. Предположим, что хранилище файлов Azure поддерживает протокол SMB. В результате вы можете сопоставить локальный виртуальный диск с общей папкой хранилища файлов Azure с помощью следующей процедуры:
1.  Создайте учетную запись хранилища файлов (например, `mystorage`), общую папку (например, `sharejson`), а также папку в хранилище файлов Azure с помощью портала Azure или Azure PowerShell.
2.  Отправьте несколько файлов JSON в общую папку хранилища файлов.
3.  Создайте исходящее правило брандмауэра в брандмауэре Windows на компьютере, где разрешен доступ к порту 445. Имейте в виду, что ваш поставщик услуг Интернета может заблокировать этот порт. Если вы получите уведомление об ошибке DNS (ошибка 53), выполняя последующие действия, это значит, что порт 445 закрыт или блокируется поставщиком.
4. Подключите общую папку хранилища файлов Azure как локальный диск (например, `T:`).

    Синтаксис команды имеет следующий вид:

    ```dos
    net use [drive letter] \\[storage name].file.core.windows.net\[share name] /u:[storage account name] [storage account access key]
    ```

    Ниже показан пример, в котором общей папке хранилища файлов Azure назначается буква локального диска `T:`:

    ```dos
    net use t: \\mystorage.file.core.windows.net\sharejson /u:myaccount hb5qy6eXLqIdBj0LvGMHdrTiygkjhHDvWjUZg3Gu7bubKLg==
    ```

    Ключ учетной записи хранения и первичный или вторичный ключ доступа к этой записи находятся в разделе ключей в настройках на портале Azure.

5.  Теперь доступ к JSON-файлам можно получить из общей папки хранилища файлов Azure с помощью подключенного диска, как показано в следующем примере.

    ```sql
    SELECT book.* FROM
     OPENROWSET(BULK N't:\books\books.json', SINGLE_CLOB) AS json
     CROSS APPLY OPENJSON(BulkColumn)
     WITH( id nvarchar(100), name nvarchar(100), price float,
        pages_i int, author nvarchar(100)) AS book
    ```

Дополнительные сведения о хранилище файлов Azure см. на [этой странице](https://azure.microsoft.com/en-us/services/storage/files/).

## <a name="import-json-documents-from-azure-blob-storage"></a>Импорт документов JSON из хранилища BLOB-объектов Azure

Вы можете загрузить файлы напрямую в базу данных SQL Azure из хранилища BLOB-объектов Azure с помощью команды T-SQL BULK INSERT и функции OPENROWSET.

Сначала необходимо создать внешний источник данных, как показано в примере ниже.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
 WITH ( TYPE = BLOB_STORAGE,
        LOCATION = 'https://myazureblobstorage.blob.core.windows.net',
        CREDENTIAL= MyAzureBlobStorageCredential);
```

Затем выполните команду BULK INSERT с использованием функции DATA_SOURCE.

```sql
BULK INSERT Product
FROM 'data/product.dat'
WITH ( DATA_SOURCE = 'MyAzureBlobStorage');
```

Дополнительные сведения и пример использования функции OPENROWSET см. в статье [Loading files from Azure Blob Storage into Azure SQL Database](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/02/23/loading-files-from-azure-blob-storage-into-azure-sql-database/) (Загрузка файлов из хранилища BLOB-объектов Azure в базу данных SQL Azure).

## <a name="parse-json-documents-into-rows-and-columns"></a>Синтаксический анализ документов JSON с преобразованием в строки и столбцы
Вместо того чтобы считывать весь файл JSON как отдельное значение, вы можете выполнить его синтаксический анализ и вернуть названия книг из файла и их свойства в виде строк и столбцов. В следующем примере используется JSON-файл с [этого сайта](https://github.com/tamingtext/book/blob/master/apache-solr/example/exampledocs/books.json), содержащий список документации.

### <a name="example-1"></a>Пример 1
В самом простом случае вы можете просто загрузить весь список из файла. 

```sql
SELECT value
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
```

### <a name="example-2"></a>Пример 2
OPENROWSET считывает отдельное текстовое значение из файла, возвращает его как BulkColumn и передает функции OPENJSON. OPENJSON перебирает массив объектов JSON в массиве BulkColumn и возвращает по одной книге на строку в формате JSON:

```json
{"id":"978-0641723445″, "cat":["book","hardcover"], "name":"The Lightning Thief", … 
{"id":"978-1423103349″, "cat":["book","paperback"], "name":"The Sea of Monsters", … 
{"id":"978-1857995879″, "cat":["book","paperback"], "name":"Sophie’s World : The Greek … 
{"id":"978-1933988177″, "cat":["book","paperback"], "name":"Lucene in Action, Second … 
```

### <a name="example-3"></a>Пример 3
С помощью функции OPENJSON можно выполнять синтаксический анализ содержимого JSON и преобразовывать его в таблицу или результирующий набор. В примере ниже показана загрузка содержимого, синтаксический анализ загруженного содержимого JSON и возвращение пяти полей в качестве столбцов.

```sql
SELECT book.*
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
 WITH( id nvarchar(100), name nvarchar(100), price float,
 pages_i int, author nvarchar(100)) AS book
```

В этом примере функция OPENROWSET(BULK) считывает содержимое файла и передает его функции OPENJSON с помощью определенной схемы вывода. OPENJSON сопоставляет свойства в объектах JSON с помощью имен столбцов. Например, свойство `price` возвращается как столбец `price` и преобразовывается в тип данных float. Результаты приведены ниже.

|Идентификатор|Имя|price|pages_i|Автор
|---|---|---|---|---|
978-0641723445|The Lightning Thief|12.5|384|Рик Риордан (Rick Riordan)| 
978-1423103349|The Sea of Monsters|6.49|304|Рик Риордан (Rick Riordan)| 
978-1857995879|Sophie’s World: The Greek Philosophers|3.07|64|Юстейн Гордер (Jostein Gaarder)| 
978-1933988177|Lucene in Action, Second Edition|30.5|475|Майкл Маккэндлесс (Michael McCandless)|
||||||

Теперь вы можете вернуть эту таблицу пользователю или загрузить данные в другую таблицу.

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).
  
## <a name="see-also"></a>См. также:
[Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)


