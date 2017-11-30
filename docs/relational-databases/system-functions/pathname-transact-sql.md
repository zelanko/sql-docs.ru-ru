---
title: "PathName (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PathName_TSQL
- PathName
dev_langs: TSQL
helpviewer_keywords: PathName FILESTREAM [SQL Server]
ms.assetid: 6b95ad90-6c82-4a23-9294-a2adb74934a3
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 029ba3a0508e3198b3b81e94a508783308a4257d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="pathname-transact-sql"></a>PathName (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает путь в виде большого двоичного объекта (BLOB) FILESTREAM. OpenSqlFilestream API использует этот путь возвращает дескриптор, приложение может использовать для работы с данными большого двоичного ОБЪЕКТА с помощью API-интерфейсов Win32. Функция PathName доступна только для чтения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
column_name.PathName ( @option [ , use_replica_computer_name ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *column_name*  
 Имя столбца **varbinary(max)** столбец FILESTREAM. *column_name* должно быть именем столбца. Он не может быть выражением или результатом инструкции CAST или CONVERT.  
  
 PathName для столбца, в любой другой тип данных или для **varbinary(max)** columnthat не вызывают ошибку компиляции запроса будет атрибут хранилища FILESTREAM.  
  
 *@option*  
 Целое число [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , определяющий способ форматирования серверных компонентов пути. *@option*может принимать одно из следующих значений. Значение по умолчанию равно 0.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Пример возвращает имя сервера, преобразовать в BIOS форматирование.`\\SERVERNAME\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F19F7-38EA-4AB0-BB89-E6C545DBD3F9`|  
|1|Возвращает имя сервера без преобразования, например:`\\ServerName\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F1`|  
|2|Возвращает полный путь сервера, например:`\\ServerName.MyDomain.com\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F19F7-38EA-4AB0-BB89-E6C545DBD3F9`|  
  
 *use_replica_computer_name*  
 Битовое значение, определяет, как следует возвращать имя сервера в группе доступности Always On.  
  
 Если базы данных не принадлежит к группе доступности Always On, значение этого аргумента игнорируется. В пути всегда используется имя компьютера.  
  
 Если база данных принадлежит доступности Always On группы, затем значение *use_replica_computer_name* приведет к следующим последствиям на выходе **PathName** функции:  
  
|Значение|Description|  
|-----------|-----------------|  
|Не указано.|Функция возвращает в пути имя виртуальной сети.|  
|0|Функция возвращает в пути имя виртуальной сети.|  
|1|Функция возвращает в пути имя компьютера.|  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **nvarchar(max)**  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение является полным логическим путем или путем NETBIOS объекта BLOB. PathName не возвращает IP-адрес. Возвращается значение NULL, если объект FILESTREAM BLOB не создан.  
  
## <a name="remarks"></a>Замечания  
 Столбец ROWGUID должен быть виден любому запросу, который вызывает функцию PathName.  
  
 Объект FILESTREAM BLOB можно создать только с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-reading-the-path-for-a-filestream-blob"></a>A. Считывание пути для объекта FILESTREAM BLOB  
 В следующем примере значение функции `PathName` присваивается переменной типа `nvarchar(max)`.  
  
```tsql  
DECLARE @PathName nvarchar(max);  
SET @PathName = (  
    SELECT TOP 1 photo.PathName()  
    FROM dbo.Customer  
    WHERE LastName = 'CustomerName'  
    );  
```  
  
### <a name="b-displaying-the-paths-for-filestream-blobs-in-a-table"></a>Б. Отображение путей объектов FILESTREAM BLOB в таблице  
 В следующем примере создаются и отображаются пути трех объектов FILESTREAM BLOB.  
  
```tsql  
-- Create a FILESTREAM-enabled database.  
-- The c:\data directory must exist.  
CREATE DATABASE PathNameDB  
ON  
PRIMARY ( NAME = ArchX1,  
    FILENAME = 'c:\data\archdatP1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = ArchX3,  
    FILENAME = 'c:\data\filestreamP1')  
LOG ON  ( NAME = ArchlogX1,  
    FILENAME = 'c:\data\archlogP1.ldf');  
GO  
  
USE PathNameDB;  
GO  
  
-- Create a table, add some records, and  
-- create the associated FILESTREAM  
-- BLOB files.  
  
CREATE TABLE TABLE1  
    (  
        ID int,  
        RowGuidColumn UNIQUEIDENTIFIER  
                      NOT NULL UNIQUE ROWGUIDCOL,  
        FILESTREAMColumn varbinary(MAX) FILESTREAM  
    );  
GO  
  
INSERT INTO TABLE1 VALUES  
 (1, NEWID(), 0x00)  
,(2, NEWID(), 0x00)  
,(3, NEWID(), 0x00);  
GO  
  
SELECT FILESTREAMColumn.PathName() AS 'PathName' FROM TABLE1;  
  
--Results  
--PathName  
------------------------------------------------------------------------------------------------------------  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\DD67C792-916E-4A76-8C8A-4A85DC5DB908  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\2907122B-2560-4CB9-86DC-FBE7ABA1843B  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\922BE0E0-CAB9-4403-90BF-945BD258E4BC  
--  
--(3 row(s) affected)  
GO  
  
--Drop the database to clean up.  
USE master;  
GO  
DROP DATABASE PathNameDB;  
```  
  
## <a name="see-also"></a>См. также:  
 [Большой двоичный объект &#40;BLOB-объект&#41;Данные&#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [GET_FILESTREAM_TRANSACTION_CONTEXT &#40; Transact-SQL &#41;](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md)   
 [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
  
