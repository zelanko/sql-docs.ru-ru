---
description: SIGNBYCERT (Transact-SQL)
title: SIGNBYCERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIGNBYCERT
- SIGNBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text signing [SQL Server]
- encryption [SQL Server], certificates
- certificates [SQL Server], text signing
- SignByCert function
- signing text [SQL Server]
- SIGNBYCERT function
- cryptography [SQL Server], certificates
ms.assetid: b4c6bced-4473-4bae-85b9-56deced495f9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: acc73e861b0c27b4a1fa46e7c4c2efa0e23cb55d
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91378931"
---
# <a name="signbycert-transact-sql"></a>SIGNBYCERT (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Подписывает текст сертификатом и возвращает подпись.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql 
SignByCert ( certificate_ID , @cleartext [ , 'password' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *certificate_ID*  
 Идентификатор сертификата в текущей базе данных. Аргумент *certificate_ID* имеет тип **int**.  
  
 *\@cleartext*  
 Переменная типа **nvarchar**, **char**, **varchar** или **nchar**, содержащая данные, которые будут подписаны.  
  
 **'** *password* **'**  
 Пароль, при помощи которого был зашифрован закрытый ключ сертификата. Аргумент *password* имеет тип **nvarchar(128)**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Комментарии  
 Требует разрешения CONTROL для сертификата.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере текст переменной `@SensitiveData` подписывается сертификатом `ABerglundCert07` после расшифровки сертификата с помощью пароля "pGFD4bb925DGvbd2439587y". Затем открытый текст и подпись вставляются в таблицу `SignedData04`.  
  
```sql  
DECLARE @SensitiveData NVARCHAR(max);  
SET @SensitiveData = N'Saddle Price Points are   
    2, 3, 5, 7, 11, 13, 17, 19, 23, 29';  
INSERT INTO [SignedData04]  
    VALUES( N'data signed by certificate ''ABerglundCert07''',  
    @SensitiveData, SignByCert( Cert_Id( 'ABerglundCert07' ),   
    @SensitiveData, N'pGFD4bb925DGvbd2439587y' ));  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [VERIFYSIGNEDBYCERT (Transact-SQL)](../../t-sql/functions/verifysignedbycert-transact-sql.md)   
 [CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
