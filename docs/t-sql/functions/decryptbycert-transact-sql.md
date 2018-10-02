---
title: DECRYPTBYCERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff7cd9e82f2e70e39b02f10726acbae657ad670c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741202"
---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция расшифровывает зашифрованные данные с помощью закрытого ключа сертификата.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *certificate_ID*  
Идентификатор сертификата в базе данных. *certificate_ID* имеет тип данных **int**.  
  
 *ciphertext*  
Строка данных, зашифрованная с помощью открытого ключа сертификата.  
  
 @ciphertext  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью сертификата.  
  
 *cert_password*  
Пароль, используемый для шифрования закрытого ключа сертификата. *cert_password* должен иметь формат данных Юникода.  
  
 @cert_password  
Переменная типа **nchar** или **nvarchar**, содержащая пароль, используемый для шифрования закрытого ключа сертификата. *@cert_password* должен иметь формат данных Юникода.  

## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Эта функция расшифровывает данные при помощи закрытого ключа сертификата. Криптографические преобразования с использованием асимметричных ключей требуют значительных ресурсов. Поэтому мы не рекомендуем разработчикам использовать функции [ENCRYPTBYCERT](./encryptbycert-transact-sql.md) и DECRYPTBYCERT для шифрования и расшифровки обычных данных пользователей.  

## <a name="permissions"></a>Разрешения  
`DECRYPTBYCERT` требует разрешения CONTROL для сертификата.  
  
## <a name="examples"></a>Примеры  
В этом примере выбираются строки из `[AdventureWorks2012].[ProtectedData04]`, помеченного как данные, изначально зашифрованные с помощью сертификата `JanainaCert02`. Сначала выполняется расшифровка закрытого ключа сертификата `JanainaCert02` с помощью пароля сертификата `pGFD4bb925DGvbd2439587y`. Затем с помощью этого закрытого ключа расшифровывается зашифрованный текст. Расшифрованные данные преобразуются из типа **varbinary** в тип **nvarchar**.  

```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ENCRYPTBYCERT (Transact-SQL)](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
