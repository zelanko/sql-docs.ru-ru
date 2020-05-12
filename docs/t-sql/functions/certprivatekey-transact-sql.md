---
title: CERTPRIVATEKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7a8bf334be11a219dccf84f6732fb94254034403
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832198"
---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Эта функция возвращает закрытый ключ сертификата в двоичном формате. Эта функция принимает три аргумента.
-   Идентификатор сертификата.  
-   Пароль, используемый для шифрования битов закрытого ключа, возвращаемых этой функцией. При таком подходе ключи не предоставляются пользователям в виде открытого текста.  
-   Необязательный пароль расшифровки. Указанный пароль расшифровки используется для расшифровки закрытого ключа этого сертификата. В противном случае используется главный ключ базы данных.  
  
Эту функцию могут использовать только пользователи с доступом к закрытому ключу сертификата. Эта функция возвращает закрытый ключ в формате ПВК.
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Аргументы  
*certificate_ID*  
Идентификатор **certificate_id** сертификата. Это значение можно получить из sys.certificates или через вызов функции [CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md). *cert_id* имеет тип данных **int**.
  
*encryption_password*  
Пароль, используемый для шифрования возвращаемого двоичного значения.
  
*decryption_password*  
Пароль, используемый для расшифровки возвращаемого двоичного значения.
  
## <a name="return-types"></a>Типы возвращаемых данных
**varbinary**
  
## <a name="remarks"></a>Remarks  
Функции **CERTENCODED** и **CERTPRIVATEKEY** используются совместно для возврата различных составляющих сертификата в двоичной форме.
  
## <a name="permissions"></a>Разрешения  
Функция **CERTPRIVATEKEY** общедоступна.
  
## <a name="examples"></a>Примеры  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20401031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Пример использования функций [CERTPRIVATEKEY](../../t-sql/functions/certencoded-transact-sql.md) и **CERTENCODED** для копирования сертификата в другую базу данных см. в примере Б из статьи **CERTENCODED (Transact-SQL)** .
  
## <a name="see-also"></a>См. также раздел
[Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)
[Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)
[sys.certificates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
