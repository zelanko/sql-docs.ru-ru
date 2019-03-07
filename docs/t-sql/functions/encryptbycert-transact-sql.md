---
title: ENCRYPTBYCERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYCERT
- ENCRYPTBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], encryption
- encryption [SQL Server], certificates
- ENCRYPTBYCERT function
ms.assetid: ab66441f-e2d2-4e3a-bcae-bcc09e12f3c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79530fff04d278d9dbc8e1ad1454bc4dca4c885c
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662948"
---
# <a name="encryptbycert-transact-sql"></a>ENCRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Шифрует данные на открытом ключе сертификата.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EncryptByCert ( certificate_ID , { 'cleartext' | @cleartext } )  
```  
  
## <a name="arguments"></a>Аргументы  
_certificate\_ID_  
Идентификатор сертификата в базе данных. **int**.  
  
_cleartext_  
Строка, содержимое которой будет зашифровано с помощью сертификата.  
  
**@cleartext**  
Переменная одного из следующих типов, данные которой будут зашифрованы с помощью открытого ключа сертификата:

* **nvarchar** 
* **char**
* **varchar**
* **binary** 
* **varbinary**
* **nchar**
  
## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Эта функция шифрует данные при помощи открытого ключа сертификата. Код может быть расшифрован только с помощью соответствующего закрытого ключа. Такие ассиметричные преобразования обходятся дороже, чем шифрование и дешифрование с использованием симметричного ключа. Поэтому использование ассиметричного шифрования не рекомендуется при работе с большими наборами данных.
  
## <a name="examples"></a>Примеры  
В этом примере неформатированный текст из переменной `@cleartext` шифруется сертификатом с именем `JanainaCert02`. Зашифрованные данные помещаются в таблицу `ProtectedData04`.  
  
```  
INSERT INTO [AdventureWorks2012].[ProtectedData04]   
    VALUES ( N'Data encrypted by certificate ''Shipping04''',  
    EncryptByCert(Cert_ID('JanainaCert02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DECRYPTBYCERT (Transact-SQL)](../../t-sql/functions/decryptbycert-transact-sql.md)   
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
[ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
[DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
[BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
[Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
