---
description: OBJECT_DEFINITION (Transact-SQL)
title: OBJECT_DEFINITION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OBJECT_DEFINITION_TSQL
- OBJECT_DEFINITION
dev_langs:
- TSQL
helpviewer_keywords:
- viewing source text
- source text [SQL Server]
- displaying source text
- OBJECT_DEFINITION function
ms.assetid: 2ac837c7-eca9-4d29-b06e-72e30450c68d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 239a48b378e186e6149a31012785835939d2cde7
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115948"
---
# <a name="object_definition-transact-sql"></a>OBJECT_DEFINITION (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает исходный текст [!INCLUDE[tsql](../../includes/tsql-md.md)] определения указанного объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
OBJECT_DEFINITION ( object_id )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *object_id*  
 Идентификатор объекта, который будет использован. Аргумент *object_id* имеет тип **int** и представляет объект, который находится в контексте текущей базы данных.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar(max)**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как OBJECT_DEFINITION, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Комментарии  
 Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] предполагает, что объект с идентификатором *object_id* находится в контексте текущей базы данных. Параметры сортировки определения объекта всегда совпадают с параметрами сортировки контекста вызывающей базы данных.  
  
 OBJECT_DEFINITION применяется к объектам следующих типов:  
  
-   C = проверочное ограничение;  
  
-   D = значение по умолчанию (ограничение или изолированное);  
  
-   P = хранимая процедура SQL  
  
-   FN = скалярная функция SQL  
  
-   R = правило  
  
-   RF = процедура фильтра репликации;  
  
-   TR = триггер SQL (триггер DML, существующий в пределах схемы, или триггер DDL в области базы данных или сервера);  
  
-   IF = встроенная функция SQL с табличным значением  
  
-   TF = возвращающая табличное значение функция SQL;  
  
-   V = представление  
  
## <a name="permissions"></a>Разрешения  
 Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или получателям, которым предоставлено одно из следующих разрешений: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION. Эти разрешения неявно предоставляются членам предопределенных ролей базы данных **db_owner**, **db_ddladmin**и **db_securityadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-source-text-of-a-user-defined-object"></a>A. Возвращение исходного текста пользовательского объекта  
 В следующем примере возвращается определение пользовательского триггера `uAddress` в схеме `Person`. Встроенная функция `OBJECT_ID` используется, чтобы передать идентификатор объекта триггера в инструкцию `OBJECT_DEFINITION`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.uAddress')) AS [Trigger Definition];   
GO  
```  
  
### <a name="b-returning-the-source-text-of-a-system-object"></a>Б. Возвращение исходного текста системного объекта  
 В следующем примере возвращается определение системной хранимой процедуры `sys.sp_columns`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'sys.sp_columns')) AS [Object Definition];  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_NAME (Transact-SQL)](../../t-sql/functions/object-name-transact-sql.md)   
 [OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
  
