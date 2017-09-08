---
title: "Изменение ВНЕШНЕГО источника данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: f74a105226f1ae113287f1c337c1c33e81bb09ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="alter-external-data-source-transact-sql"></a>Изменение ВНЕШНЕГО источника данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Изменение внешнего источника данных используется для создания внешней таблицы. Внешний источник данных может быть Hadoop или BLOB-объекта хранилища Azure (WASB).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Modify an external data source
-- Applies to: SQL Server (2016 or later), Azure SQL Data Warehouse,
               Parallel Data Warehouse    
ALTER EXTERNAL DATA SOURCE data_source_name SET  
    {   
        LOCATION = 'server_name_or_IP' [,] |  
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |  
        CREDENTIAL = credential_name  
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017), Azure SQL Database,
               Azure SQL Data Warehouse, Parallel Data Warehouse
ALTER EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Аргументы  
 имя_источника_данных  
 Задает пользовательское имя для источника данных. Имя должно быть уникальным.  
  
 РАСПОЛОЖЕНИЕ = «server_name_or_IP»  
 Указывает имя сервера или IP-адрес.  
  
 RESOURCE_MANAGER_LOCATION = "\<IP-адрес; Порт > "  
 Указывает расположение диспетчера ресурсов Hadoop. Если указано, оптимизатор запросов может выбрать для предварительной обработки данных для запросов PolyBase с использованием Hadoop вычислительные мощности. Это решение, основанный на стоимости. Вызывается Включение предиката, это может значительно сократить объем данных, передаваемых между Hadoop и SQL и таким образом повысить производительность запросов.  
  
 Учетные данные = Credential_Name  
 Указывает именованный учетные данные. В разделе [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  

ТИП = BLOB_STORAGE   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Для массовых операций, `LOCATION` должен быть допустимым URL-адрес хранилища больших двоичных объектов Azure. Не размещайте  **/** , имя файла или общие параметры подписи доступа в конце `LOCATION` URL-адрес.   
Учетные данные, используемые, должен быть создан с помощью `SHARED ACCESS SIGNATURE` с удостоверением. Дополнительные сведения о подписанных URL-адресах см. в [этой статье](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

  
  
## <a name="remarks"></a>Замечания  
 Одновременно можно изменить только один источник. Параллельные запросы на изменение того же источника вызвать одной инструкции ожидания. Тем не менее можно изменить различных источников, в то же время. Кроме того это эту инструкцию можно выполнить параллельно с другими инструкциями.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY EXTERNAL DATA SOURCE.  
 > [!IMPORTANT]  
 >  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому участнику возможность создания и изменения любого объекта источника внешних данных, и таким образом, он также предоставляет возможность доступа к все учетные данные уровня базы данных в базе данных. Это разрешение следует рассматривать как широкими правами и поэтому должен предоставлять только доверенным участникам в системе.

  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется расположение и расположение диспетчера ресурсов существующего источника данных.  
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET  
     LOCATION = 'hdfs://10.10.10.10:8020',  
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'  
    ;  
  
```  
  
 В следующем примере изменяется учетные данные для подключения к источнику данных.  
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET  
   CREDENTIAL = new_hadoop_user  
    ;  
```  
  
  

