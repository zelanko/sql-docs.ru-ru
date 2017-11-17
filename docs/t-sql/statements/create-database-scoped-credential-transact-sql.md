---
title: "Создание учетных данных области базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE SCOPED CREDENTIAL
- DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_TSQL
- CREATE_DATABASE_SCOPED_CREDENTIAL
- CREATE_DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL
helpviewer_keywords:
- DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], DATABASE SCOPED CREDENTIAL statement
ms.assetid: fe830577-11ca-44e5-953b-2d589d54d045
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 49ff2aa300fc8f8e74424ae6e334bee823e8176c
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="create-database-scoped-credential-transact-sql"></a>Создание учетных данных области базы данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Создает учетные данные базы данных. Учетные данные базы данных не сопоставляется сервера имя входа или пользователя базы данных. Учетные данные базы данных используется для доступа к внешнее расположение, каждый раз, когда выполняет операции, требующие доступа к базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 
CREATE DATABASE SCOPED CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Задает имя создаваемого учетные данные уровня базы данных. *credential_name* не может начинаться со знака номера (#). Системные учетные данные начинаются с символов ##.  
  
 УДОСТОВЕРЕНИЕ **= "***identity_name***"**  
 Указывает имя учетной записи для использования при подключении за пределами сервера. Чтобы импортировать файл из хранилища больших двоичных объектов Azure, необходимо имя удостоверения `SHARED ACCESS SIGNATURE`.  Дополнительные сведения о подписях общего доступа см. в разделе [с помощью подписи URL (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
  
 СЕКРЕТ **= "***секрет***"**  
 Указывает секретный код, необходимый для исходящей проверки подлинности. `SECRET`необходимо импортировать файл из хранилища больших двоичных объектов Azure.   
>  [!WARNING]
>  Значение ключа SAS может начинаться с "?" (вопросительный знак). При использовании ключа SAS, необходимо удалить начальные "?". В противном случае может быть заблокирован усилий.  
  
## <a name="remarks"></a>Замечания  
 Учетные данные уровня базы данных — это запись, содержащая данные для проверки подлинности, необходимые для подключения к ресурсу за пределами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Большинство учетных данных включают имя пользователя и пароль Windows.  
  
 Для создания базы данных учетные данные области, база должна иметь главный ключ для защиты учетных данных. Дополнительные сведения см. в разделе [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md).  
  
 Если IDENTITY является пользователем Windows, секретный код может быть паролем. Секретный код шифруется главным ключом службы. Если главный ключ службы формируется повторно, секретный код повторно шифруется, используя новый главный ключ службы.  
   
 Сведения об учетных данных уровня базы данных можно увидеть в [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) представления каталога.  
  
 
 Hereare учетные данные уровня некоторые приложения базы данных:  
  
- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]использует учетные данные уровня базы данных для доступа к хранилищу больших двоичных объектов не являющиеся открытыми или кластеров Hadoop, защита Kerberos с PolyBase. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  

- [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]с помощью PolyBase, использующая учетные данные уровня базы данных для доступа к хранилищу BLOB-объектов Azure не являющиеся открытыми. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]использует базы данных с областью учетные данные для своего компонента глобального запроса. Это возможность выполнять запросы по нескольким сегментам базы данных.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]использует учетные данные уровня базы данных для записи файлов расширенных событий в хранилище BLOB-объектов Azure.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]использует базы данных с областью учетные данные для эластичных пулов. Дополнительные сведения см. в разделе [справиться взрывоподобный рост эластичных баз данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)  

- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) в области базы данных используйте учетные данные для доступа к данным из хранилища BLOB-объектов Azure. Дополнительные сведения см. в разделе [примеры массового доступ к данным в хранилище больших двоичных объектов Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md). 
  
## <a name="permissions"></a>Permissions  
 Требуется **УПРАВЛЕНИЯ** разрешения в базе данных.  
  
## <a name="examples"></a>Примеры  
### <a name="a-creating-a-database-scoped-credential-for-your-application"></a>A. Создание базы данных в области видимости учетных данных для вашего приложения.
 В следующем примере создаются учетные данные уровня базы данных с именем `AppCred`. Учетные данные уровня базы данных содержит пользователя Windows `Mary5` и пароль.  
  
```tsql  
-- Create a db master key if one does not already exist, using your own password.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';  
  
-- Create a database scoped credential.  
CREATE DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-database-scoped-credential-for-a-shared-access-signature"></a>Б. Создание базы данных в области видимости учетные данные для подписанного URL-адреса.   
В следующем примере создаются учетные данные уровня базы данных, которые можно использовать для создания [внешнего источника данных](../../t-sql/statements/create-external-data-source-transact-sql.md), который можно сделать объема массовых операций, таких как [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Подписи общего доступа не может использоваться с PolyBase в SQL Server, APS или хранилища данных SQL.
```tsql
CREATE DATABASE SCOPED CREDENTIAL MyCredentials  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```
  
### <a name="c-creating-a-database-scoped-credential-for-polybase-connectivity-to-azure-data-lake-store"></a>В. Создание базы данных в области видимости учетные данные для подключения к PolyBase для хранилища Озера данных Azure.  
В следующем примере создаются учетные данные уровня базы данных, которые можно использовать для создания [внешнего источника данных](../../t-sql/statements/create-external-data-source-transact-sql.md), который может использоваться PolyBase в хранилище данных SQL Azure.

Хранилище Озера данных Azure использует приложение Azure Active Directory для проверки подлинности служб.
Проверьте [создать приложение AAD](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory) и задокументировать ваши client_id, OAuth_2.0_Token_EndPoint и ключ, прежде чем пытаться создать учетные данные уровня базы данных.

```tsql
CREATE DATABASE SCOPED CREDENTIAL ADL_User
WITH
    IDENTITY = '<client_id>@\<OAuth_2.0_Token_EndPoint>'
    SECRET = '<key>'
;
```  
  
  
  
## <a name="more-information"></a>Дополнительные сведения  
 [Учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

