---
title: "ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91224c6e96fb3ee3962331ec6f378ea9aad1a5b5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-scoped-credential-transact-sql"></a>ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Учетные данные области изменения свойств базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Имя изменяемой учетные данные уровня базы данных.  
  
 УДОСТОВЕРЕНИЕ **= "***identity_name***"**  
 Указывает имя учетной записи для использования при подключении за пределами сервера. Чтобы импортировать файл из хранилища больших двоичных объектов Azure, необходимо имя удостоверения `SHARED ACCESS SIGNATURE`.  Дополнительные сведения о подписях общего доступа см. в разделе [с помощью подписи URL (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
    
  
 СЕКРЕТ **= "***секрет***"**  
 Указывает секретный код, необходимый для исходящей проверки подлинности. *секрет* необходимо импортировать файл из хранилища больших двоичных объектов Azure. *секрет* может быть необязательным для других целей.   
>  [!WARNING]
>  Значение ключа SAS может начинаться с "?" (вопросительный знак). При использовании ключа SAS, необходимо удалить начальные "?". В противном случае может быть заблокирован усилий.    
  
## <a name="remarks"></a>Замечания  
 Когда уровня базы данных учетных данных изменяется, значения *identity_name* и *секрет* сбрасываются. Если необязательный аргумент SECRET не указан, значение хранимого секретного кода устанавливается в NULL.  
  
 Секретный код шифруется с использованием главного ключа службы. Если главный ключ службы формируется заново, то секретный код шифруется повторно с использованием нового ключа.  
  
 Сведения об учетных данных уровня базы данных можно увидеть в [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) представления каталога.  
  
## <a name="permissions"></a>Permissions  
 Требуется `ALTER` разрешений на учетные данные.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. Изменение пароля базы данных учетные данные области  
 Следующий пример изменяет секретный код, хранимый в учетных данных уровня базы данных называется `Saddles`. Учетные данные уровня базы данных содержат имя входа Windows `RettigB` и его пароль. Новый пароль добавляется в учетные данные уровня базы данных с помощью предложения SECRET.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>Б. Удаление пароля из учетных данных  
 Следующий пример удаляет пароль из учетных данных уровня базы данных с именем `Frames`. Учетные данные уровня базы данных содержат имя входа Windows `Aboulrus8` и пароль. После выполнения инструкции, учетные данные уровня базы данных будет иметь пароль со значением NULL, потому что параметр SECRET не указан.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Создание учетных данных области базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

