---
title: "ALTER SYMMETRIC KEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SYMMETRIC KEY
- ALTER_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- modifying symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], modifying
- cryptography [SQL Server], symmetric keys
- ALTER SYMMETRIC KEY statement
ms.assetid: d3c776a4-7d71-4e6f-84fc-1db47400c465
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 131fb5da53d4808836f94ee85f1c07134b98b626
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-symmetric-key-transact-sql"></a>ALTER SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет свойства симметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER SYMMETRIC KEY Key_name <alter_option>  
  
<alter_option> ::=  
   ADD ENCRYPTION BY <encrypting_mechanism> [ , ... n ]  
   |   
   DROP ENCRYPTION BY <encrypting_mechanism> [ , ... n ]  
<encrypting_mechanism> ::=  
   CERTIFICATE certificate_name  
   |  
   PASSWORD = 'password'  
   |  
   SYMMETRIC KEY Symmetric_Key_Name  
   |  
   ASYMMETRIC KEY Asym_Key_Name  
```  
  
## <a name="arguments"></a>Аргументы  
 *Key_name*  
 Имя, под которым изменяемый симметричный ключ известен в базе данных.  
  
 ADD ENCRYPTION BY  
 Добавляет шифрование при помощи указанного метода.  
  
 DROP ENCRYPTION BY  
 Отменяет шифрование при помощи указанного метода. Все виды шифрования из симметричного ключа удалить нельзя.  
  
 СЕРТИФИКАТ *имя_сертификата*  
 Указывает сертификат, используемый для шифрования симметричного ключа. Этот сертификат уже должен существовать в базе данных.  
  
 ПАРОЛЬ **= "***пароль***"**  
 Указывает пароль, используемый для шифрования симметричного ключа. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 СИММЕТРИЧНЫЙ ключ *Symmetric_Key_Name*  
 Указывает симметричный ключ, используемый для шифрования изменяемого симметричного ключа. Симметричный ключ уже должен существовать в базе данных и быть открытым.  
  
 АСИММЕТРИЧНЫЙ ключ *Asym_Key_Name*  
 Указывает асимметричный ключ, используемый для шифрования изменяемого симметричного ключа. Асимметричный ключ должен уже существовать в базе данных.  
  
## <a name="remarks"></a>Замечания  
  
> [!CAUTION]  
>  Если шифрование симметричного ключа выполняется не с открытым ключом главного ключа базы данных, а с паролем, используется алгоритм шифрования TRIPLE_DES. Поэтому ключи, созданные с помощью сильных алгоритмов шифрования, таких как AES, защищены с помощью более слабого алгоритма.  
  
 Для изменения шифрования симметричного ключа используйте предложения ADD ENCRYPTION и DROP ENCRYPTION. Невозможно, чтобы ключу не соответствовал никакой способ шифрования. Поэтому оптимальным способом изменения метода шифрования является добавление новой формы шифрования и затем удаление старой.  
  
 Чтобы изменить владельца симметричного ключа, используйте [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения ALTER на симметричный ключ. При добавлении шифрования по сертификату или асимметричному ключу необходимо разрешение VIEW DEFINITION на сертификат или асимметричный ключ. При удалении шифрования по сертификату или асимметричному ключу необходимо разрешение CONTROL на сертификат или асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется метод шифрования, используемый для защиты симметричного ключа. Шифрование симметричного ключа `JanainaKey043` производится при помощи сертификата `Shipping04` во время создания этого ключа. Так как ключ никогда не может храниться незашифрованным, в этом примере шифрование добавляется по паролю, а удаляется шифрование по сертификату.  
  
```  
CREATE SYMMETRIC KEY JanainaKey043 WITH ALGORITHM = AES_256   
    ENCRYPTION BY CERTIFICATE Shipping04;  
-- Open the key.   
OPEN SYMMETRIC KEY JanainaKey043 DECRYPTION BY CERTIFICATE Shipping04  
    WITH PASSWORD = '<enterStrongPasswordHere>';   
-- First, encrypt the key with a password.  
ALTER SYMMETRIC KEY JanainaKey043   
    ADD ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';  
-- Now remove encryption by the certificate.  
ALTER SYMMETRIC KEY JanainaKey043   
    DROP ENCRYPTION BY CERTIFICATE Shipping04;  
CLOSE SYMMETRIC KEY JanainaKey043;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

