---
title: "CERTPRIVATEKEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a44f9203f9242a8f90ce3ca667bc1fea479dc2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает закрытый ключ сертификата в двоичном формате. Эта функция принимает три аргумента.
-   Идентификатор сертификата.  
-   Пароль шифрования, который используется для шифрования возвращаемых функцией битов закрытого ключа, чтобы ключи не передавались пользователям в виде открытого текста.  
-   Необязательный пароль для дешифрования. Если пароль дешифрования указан, то он используется для расшифровки закрытого ключа сертификата, в противном случае используется главный ключ базы данных.  
  
Только пользователи с доступом к закрытому ключу сертификата смогут использовать эту функцию. Эта функция возвращает закрытый ключ в формате ПВК.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Аргументы  
*идентификатор_сертификата*  
— **Идентификатор_сертификата** сертификата. Этот параметр доступен из sys.certificates или с помощью [CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) функции. *Cert_ID* — тип **int**
  
*encryption_password*  
Пароль, используемый для шифрования возвращаемого двоичного значения.
  
*decryption_password*  
Пароль, используемый для расшифровки возвращаемого двоичного значения.
  
## <a name="return-types"></a>Возвращаемые типы
**varbinary**
  
## <a name="remarks"></a>Замечания  
**CERTENCODED** и **CERTPRIVATEKEY** используются совместно для возврата различных составляющих сертификата в двоичной форме.
  
## <a name="permissions"></a>Permissions  
**CERTPRIVATEKEY** общедоступна.
  
## <a name="examples"></a>Примеры  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20141031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Более сложный пример, использующий **CERTPRIVATEKEY** и **CERTENCODED** для копирования сертификата в другую базу данных, см. пример Б в разделе [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md).
  
## <a name="see-also"></a>См. также:
[Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[СОЗДАТЬ СЕРТИФИКАТ &#40; Transact-SQL &#41; ](../../t-sql/statements/create-certificate-transact-sql.md) 
 [Функции безопасности &#40; Transact-SQL &#41; ](../../t-sql/functions/security-functions-transact-sql.md) 
 [sys.certificates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  

