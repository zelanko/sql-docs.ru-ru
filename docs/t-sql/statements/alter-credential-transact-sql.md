---
title: ALTER CREDENTIAL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER CREDENTIAL
- ALTER_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], credentials
- credentials [SQL Server], ALTER CREDENTIAL statement
- modifying credentials
- authentication [SQL Server], credentials
- ALTER CREDENTIAL statement
ms.assetid: b08899a6-c09e-4af4-91aa-a978ada79264
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: a85ee103b2a50f75b3157e4fdb1b29b88dbf7258
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895728"
---
# <a name="alter-credential-transact-sql"></a>ALTER CREDENTIAL (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Изменяет свойства учетных данных.  

> [!IMPORTANT]
> Соглашения из статьи о ![значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [синтаксических обозначениях в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md) можно использовать как рекомендации или как инструкции для задачи.  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
ALTER CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Имя, связанное с изменяемыми учетными данными.  
  
 IDENTITY **='***identity_name***'**  
 Указывает имя учетной записи для использования при подключении за пределами сервера.  
  
 SECRET **='***secret***'**  
 Указывает секретный код, необходимый для исходящей проверки подлинности. Аргумент *secret* является необязательным.
  
> [!IMPORTANT]
> База данных SQL Azure поддерживает только удостоверения Azure Key Vault и удостоверения на основе подписанного URL-адреса. Удостоверения пользователей Windows не поддерживаются.
  
## <a name="remarks"></a>Remarks  
 При изменении учетных данных значения *identity_name* и *secret* сбрасываются. Если необязательный аргумент SECRET не указан, значение хранимого секретного кода устанавливается в NULL.  
  
 Секретный код шифруется с использованием главного ключа службы. Если главный ключ службы формируется заново, то секретный код шифруется повторно с использованием нового ключа.  
  
 Сведения об учетных данных отображаются в представлении каталога **sys.credentials**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY CREDENTIAL. Если учетные данные являются системными, требуется разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-password-of-a-credential"></a>A. Изменение пароля учетных данных  
 Следующий пример изменяет секретный код, хранимый в учетных данных, связанных с именем `Saddles`. Учетные данные содержат имя входа Windows `RettigB` и пароль пользователя. Новый пароль добавляется в учетные данные с помощью предложения SECRET.  
  
```  
ALTER CREDENTIAL Saddles WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>Б. Удаление пароля из учетных данных  
 Следующий пример удаляет пароль из учетных данных, связанных с именем `Frames`. Учетные данные содержат имя входа Windows `Aboulrus8` и пароль. После выполнения этой инструкции учетные данные будут включать пароль со значением NULL, потому что параметр SECRET не указан.  
  
```  
ALTER CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [DROP CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
