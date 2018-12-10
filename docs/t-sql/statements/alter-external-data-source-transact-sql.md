---
title: ALTER EXTERNAL DATA SOURCE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL DATA SOURCE
- ALTER_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- polybase, alter external data source statement
- ALTER EXTERNAL DATA SOURCE statement
ms.assetid: a34b9e90-199d-46d0-817a-a7e69387bf5f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3654e06666c4b8d9639cf3d6ce792cdf80e4cdd6
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396817"
---
# <a name="alter-external-data-source-transact-sql"></a>ALTER EXTERNAL DATA SOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Изменяет внешний источник данных, используемый для создания внешней таблицы. Внешний источник данных может быть хранилищем Hadoop хранилищем BLOB-объектов Azure (WASB).
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Modify an external data source
-- Applies to: SQL Server (2016 or later)
ALTER EXTERNAL DATA SOURCE data_source_name SET
    {   
        LOCATION = 'server_name_or_IP' [,] |
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |
        CREDENTIAL = credential_name
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017)
ALTER EXTERNAL DATA SOURCE data_source_name
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Аргументы  
 data_source_name указывает определяемое пользователем имя источника данных. Имя должно быть уникальным.
  
 LOCATION = 'server_name_or_IP' — указывает имя сервера или IP-адрес.
  
 RESOURCE_MANAGER_LOCATION = '\<IP address;Port>' — указывает расположение диспетчера ресурсов Hadoop. Если аргумент указан, оптимизатор запросов может выбрать предварительную обработку данных для запросов PolyBase с помощью вычислительных мощностей Hadoop. Это решение, принимаемое на основе стоимости. Оно называется передачей предиката и может значительно сократить объем данных, передаваемых между Hadoop и SQL, повышая производительность запросов.
  
 CREDENTIAL = Credential_Name Указывает именованные учетные данные. См. раздел [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

TYPE = BLOB_STORAGE   
**Применимо к:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
Только для массовых операций — `LOCATION` должен быть допустимым URL-адресом хранилища больших двоичных объектов Azure. Не помещайте **/**, имя файла или параметры подписи общего доступа в конце URL-адреса `LOCATION`.
Используемые учетные данные необходимо создавать, используя `SHARED ACCESS SIGNATURE` в качестве удостоверения. Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

  
  
## <a name="remarks"></a>Примечания
 Одновременно можно изменить только один источник. Параллельные запросы на изменение того же источника приводят к помещению одной инструкции в режим ожидания. Однако одновременно можно изменять разные источники. Эта инструкция может выполняться параллельно с другими инструкциями.
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY EXTERNAL DATA SOURCE.
 > [!IMPORTANT]  
 >  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому субъекту возможность создания и изменения объекта внешнего источника данных и, таким образом, также предоставляет возможность доступа ко всем учетным данным уровня базы данных в базе данных. Это разрешение следует рассматривать как высоко привилегированное, поэтому его следует предоставлять только доверенным субъектам в системе.

  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется расположение и расположение диспетчера ресурсов существующего источника данных.
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
     LOCATION = 'hdfs://10.10.10.10:8020',
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'
    ;
  
```  

 В следующем примере изменяются учетные данные для подключения к источнику данных.
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
   CREDENTIAL = new_hadoop_user
    ;
```
