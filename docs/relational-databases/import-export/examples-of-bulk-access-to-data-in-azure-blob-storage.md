---
title: "Примеры массового доступа к данным в хранилище BLOB-объектов Azure | Документация Майкрософт"
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bulk importing [SQL Server], from Azure blob storage
- Azure blob storage, bulk import to SQL Server
- BULK INSERT, Azure blob storage
- OPENROWSET, Azure blob storage
ms.assetid: f7d85db3-7a93-400e-87af-f56247319ecd
caps.latest.revision: 2
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: ece80f578fc797dcd721dfb3f831e9bf3937abd1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/14/2017

---
# <a name="examples-of-bulk-access-to-data-in-azure-blob-storage"></a>Примеры массового доступа к данным в хранилище BLOB-объектов Azure
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

С помощью инструкции `BULK INSERT` и `OPENROWSET` можно непосредственно получить доступ к файлу в хранилище BLOB-объектов Azure. В следующих примерах используются данные из CSV-файла (файл данных с разделителями-запятыми) `inv-2017-01-19.csv`, который хранится в контейнере `Week3` в учетной записи хранения `newinvoices`. Вы можете использовать путь к формату файла, но он не указан в этих примерах. 

Для массового доступа к хранилищу BLOB-объектов из SQL Server требуется по крайней мере [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP версии 1.1.

## <a name="create-the-credential"></a>Создание учетных данных   
   
Для всех приведенных ниже примеров требуются учетные данные области базы данных, ссылающиеся на подписанный URL-адрес.   

>  [!IMPORTANT]
>  Внешний источник данных нужно создать с учетными данными области базы данных, использующими удостоверение `SHARED ACCESS SIGNATURE`. Для создания подписанного URL-адреса для учетной записи смотрите свойство **Подписанный URL-адрес** на странице свойств учетной записи хранения на портале Azure. Дополнительные сведения о подписанных URL-адресах см. в [этой статье](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1). Дополнительные сведения см. в статье [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
 
Создайте учетные данные области базы данных, используя параметр `IDENTITY` со значением `SHARED ACCESS SIGNATURE`. Используйте секрет с вашего портала Azure. Например:  

```sql
CREATE DATABASE SCOPED CREDENTIAL UploadInvoices  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```


## <a name="accessing-data-in-a-csv-file-referencing-an-azure-blob-storage-location"></a>Получение доступа к данным в CSV-файле, ссылающегося на расположение хранилища BLOB-объектов Azure   
В следующем примере используется внешний источник данных, указывающий на учетную запись Azure `newinvoices`.   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net', 
        CREDENTIAL = UploadInvoices  
    );
```   

Затем инструкция `OPENROWSET` добавляет имя контейнера (`week3`) к описанию файла. Имя файла — `inv-2017-01-19.csv`.
```sql     
SELECT * FROM OPENROWSET(
   BULK  'week3/inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
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
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3', 
        CREDENTIAL = UploadInvoices  
    );
```  
  
Затем `OPENROWSET` инструкция не добавляет имя контейнера к описанию файла:
```sql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoicesContainer',
   SINGLE_CLOB) AS DataFile;
```   

Не используйте имя контейнера в описании, если применяется `BULK INSERT`: 

```sql
BULK INSERT Colors2
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoicesContainer',
      FORMAT = 'CSV'); 
```

## <a name="see-also"></a>См. также:   

[CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
[CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)   
[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)   
[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)   


