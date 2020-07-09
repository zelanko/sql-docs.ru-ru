---
title: ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f76ff430e75f572378f0ed1994ed6ed204a20fa9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008490"
---
# <a name="alter-database-scoped-credential-transact-sql"></a>ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Изменяет свойства учетных данных для базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Указывает имя, связанное с изменяемыми учетными данными для базы данных.  
  
 IDENTITY **='***identity_name***'**  
 Указывает имя учетной записи для использования при подключении за пределами сервера. Чтобы импортировать файл из хранилища больших двоичных объектов Azure, необходимо имя удостоверения `SHARED ACCESS SIGNATURE`.  Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
    
  
 SECRET **='***secret***'**  
 Указывает секретный код, необходимый для исходящей проверки подлинности. *secret* требуется для импорта файла из хранилища больших двоичных объектов Azure. *secret* может указываться дополнительно в других целях.   
> [!WARNING]
>  Значение ключа SAS может начинаться с '?' (вопросительный знак). При использовании ключа SAS необходимо удалить начальный символ '?'. В противном случае действия могут быть заблокированы.    
  
## <a name="remarks"></a>Remarks  
 При изменении учетных данных для базы данных значения *identity_name* и *secret* сбрасываются. Если необязательный аргумент SECRET не указан, значение хранимого секретного кода устанавливается в NULL.  
  
 Секретный код шифруется с использованием главного ключа службы. Если главный ключ службы формируется заново, то секретный код шифруется повторно с использованием нового ключа.  
  
 Дополнительные сведения об учетных данных для базы данных см. в представлении каталога [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `ALTER` на учетные данные.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. Изменение пароля учетных данных для базы данных  
 Следующий пример изменяет секрет, хранимый в учетных данных для базы данных, с именем `Saddles`. Учетные данные для базы данных содержат имя входа Windows `RettigB` и пароль. Новый пароль добавляется в учетные данные для базы данных с помощью предложения SECRET.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>Б. Удаление пароля из учетных данных  
 Следующий пример удаляет пароль из учетных данных для базы данных с именем `Frames`. Учетные данные для базы данных содержат имя входа Windows `Aboulrus8` и пароль. После выполнения этой инструкции учетные данные для базы данных будут включать пароль со значением NULL, потому что параметр SECRET не указан.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
