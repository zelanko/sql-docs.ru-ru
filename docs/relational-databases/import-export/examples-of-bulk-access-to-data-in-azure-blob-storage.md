---
title: Массовый доступ к данным в хранилище BLOB-объектов Azure
description: Примеры Transact-SQL, использующие BULK INSERT и OPENROWSET для доступа к данным в учетной записи хранилища BLOB-объектов Azure.
ms.date: 10/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], from Azure blob storage
- Azure blob storage, bulk import to SQL Server
- BULK INSERT, Azure blob storage
- OPENROWSET, Azure blob storage
ms.assetid: f7d85db3-7a93-400e-87af-f56247319ecd
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: de82e4c1b72355fa97e1d844be45d563a4161ed5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473995"
---
# <a name="examples-of-bulk-access-to-data-in-azure-blob-storage"></a>Примеры массового доступа к данным в хранилище BLOB-объектов Azure

[!INCLUDE[sqlserver2017-asdb](../../includes/applies-to-version/sqlserver2017-asdb.md)]

С помощью инструкции `BULK INSERT` и `OPENROWSET` можно непосредственно получить доступ к файлу в хранилище BLOB-объектов Azure. В следующих примерах используются данные из CSV-файла (файл данных с разделителями-запятыми) `inv-2017-01-19.csv`, который хранится в контейнере `Week3` в учетной записи хранения `newinvoices`. Вы можете использовать путь к формату файла, но он не указан в этих примерах.

Для массового доступа к хранилищу BLOB-объектов из SQL Server требуется по крайней мере [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP версии 1.1.

> [!IMPORTANT]
> Все пути к контейнеру и к файлам в большом двоичном объекте являются `CASE SENSITIVE`. Если они не верны, может быть возвращена такая ошибка: "Массовая загрузка невозможна. Файл "file.csv" не существует или у вас нет прав на доступ к нему".

## <a name="create-the-credential"></a>Создание учетных данных

Для всех приведенных ниже примеров требуются учетные данные области базы данных, ссылающиеся на подписанный URL-адрес.

> [!IMPORTANT]
> Внешний источник данных нужно создать с учетными данными области базы данных, использующими удостоверение `SHARED ACCESS SIGNATURE`. Для создания подписанного URL-адреса для учетной записи смотрите свойство **Подписанный URL-адрес** на странице свойств учетной записи хранения на портале Azure. Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов](/azure/storage/storage-dotnet-shared-access-signature-part-1). Дополнительные сведения см. в статье [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

Создайте учетные данные области базы данных, используя параметр `IDENTITY` со значением `SHARED ACCESS SIGNATURE`. Используйте маркер SAS, созданный для учетной записи хранения больших двоичных объектов. Убедитесь, что маркер SAS не начинается с `?`, у вас есть по крайней мере разрешение на чтение для объекта, который необходимо загрузить, и срок действия не истек (все даты указаны в формате UTC).

Пример:

```sql
CREATE DATABASE SCOPED CREDENTIAL UploadInvoices
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'sv=2018-03-28&ss=b&srt=sco&sp=rwdlac&se=2019-08-31T02:25:19Z&st=2019-07-30T18:25:19Z&spr=https&sig=KS51p%2BVnfUtLjMZtUTW1siyuyd2nlx294tL0mnmFsOk%3D';
```

## <a name="accessing-data-in-a-csv-file-referencing-an-azure-blob-storage-location"></a>Получение доступа к данным в CSV-файле, ссылающегося на расположение хранилища BLOB-объектов Azure

В следующем примере используется внешний источник данных, указывающий на учетную запись Azure `MyAzureInvoices`.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net',
        CREDENTIAL = UploadInvoices
    );
```

Затем инструкция `OPENROWSET` добавляет имя контейнера (`week3`) к описанию файла. Имя файла — `inv-2017-01-19.csv`.

```sql
SELECT * FROM OPENROWSET(
   BULK 'week3/inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   FORMAT = 'CSV',
   FORMATFILE='invoices.fmt',
   FORMATFILE_DATA_SOURCE = 'MyAzureInvoices'
   ) AS DataFile;   
```

Выполнив инструкцию `BULK INSERT`, используйте контейнер и описание файла:

```sql
BULK INSERT Colors2
FROM 'week3/inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
      FORMAT = 'CSV');
```

## <a name="accessing-data-in-a-csv-file-referencing-a-container-in-an-azure-blob-storage-location"></a>Получение доступа к данным в CSV-файле, ссылающегося на контейнер хранилища BLOB-объектов Azure

В следующем примере используется внешний источник данных, указывающий на контейнер `week3` в учетной записи хранения Azure.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoicesContainer
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = UploadInvoices
    );
```

Затем `OPENROWSET` инструкция не добавляет имя контейнера к описанию файла:

```sql
SELECT * FROM OPENROWSET(
   BULK 'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoicesContainer',
   FORMAT = 'CSV',
   FORMATFILE='invoices.fmt',
   FORMATFILE_DATA_SOURCE = 'MyAzureInvoices'
   ) AS DataFile;
```

Не используйте имя контейнера в описании, если применяется `BULK INSERT`:

```sql
BULK INSERT Colors2
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoicesContainer',
      FORMAT = 'CSV');
```

## <a name="see-also"></a>См. также:

- [CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)
- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)
- [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)