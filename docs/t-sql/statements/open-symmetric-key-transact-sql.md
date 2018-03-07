---
title: "OPEN SYMMETRIC KEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPEN SYMMETRIC KEY
- OPEN_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], opening
- OPEN SYMMETRIC KEY statement
ms.assetid: ff019a7c-c373-46c7-ac43-ffb7e2ee60b3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64ae9cd8f03e31959d433377af368b675f5eeb63
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="open-symmetric-key-transact-sql"></a>OPEN SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Расшифровывает симметричный ключ и делает его доступным для использования.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPEN SYMMETRIC KEY Key_name DECRYPTION BY <decryption_mechanism>  
  
<decryption_mechanism> ::=  
    CERTIFICATE certificate_name [ WITH PASSWORD = 'password' ]  
    |  
    ASYMMETRIC KEY asym_key_name [ WITH PASSWORD = 'password' ]  
    |  
    SYMMETRIC KEY decrypting_Key_name  
    |  
    PASSWORD = 'decryption_password'  
```  
  
## <a name="arguments"></a>Аргументы  
 *Key_name*  
 Имя симметричного ключа, который нужно открыть.  
  
 СЕРТИФИКАТ *имя_сертификата*  
 Имя сертификата, закрытый ключ которого будет использоваться для расшифровки симметричного ключа.  
  
 АСИММЕТРИЧНЫЙ ключ *asym_key_name*  
 Имя асимметричного ключа, закрытый ключ которого будет использоваться для расшифровки симметричного ключа.  
  
 С ПАРОЛЕМ = "*пароль*"  
 Пароль, который использовался для шифрования закрытого ключа сертификата или ассиметричного ключа.  
  
 СИММЕТРИЧНЫЙ ключ *decrypting_key_name*  
 Имя симметричного ключа, который будет использоваться для расшифровки открываемого симметричного ключа.  
  
 ПАРОЛЬ = "*пароль*"  
 Пароль, использованный для защиты симметричного ключа.  
  
## <a name="remarks"></a>Замечания  
 Открытые симметричные ключи привязаны к сеансу, а не к контексту безопасности. Открытый ключ останется доступным, пока не будет явно закрыт или сеанс не будет прерван. Если открыт симметричный ключ, после чего произошло переключение контекста, ключ останется открытым и будет доступным в олицетворенном контексте. Сведения о симметричных ключах можно увидеть в [sys.openkeys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) представления каталога.  
  
 Если симметричный ключ был зашифрован другим ключом, сначала необходимо открыть этот ключ.  
  
 Если симметричный ключ уже открыт, что запрос является **NO_OP**.  
  
 Если пароль, сертификат или ключ для расшифровки симметричного ключа неверен, запрос завершается сбоем.  
  
 Симметричные ключи, созданные из поставщиков шифрования, не могут быть открыты. Операции шифрования и дешифрования с помощью симметричного ключа такого рода выполняются успешно без **ОТКРОЙТЕ** инструкции, так как поставщик шифрования Открытие и закрытие ключа.  
  
## <a name="permissions"></a>Permissions  
 Участник должен обладать некоторыми разрешениями на ключ и не должен иметь запрета на разрешение VIEW DEFINITION для ключа. Дополнительные требования зависят от механизма расшифровки:  
  
-   СЕРТИФИКАТ РАСШИФРОВКИ BY: Разрешение CONTROL на сертификат и пароль, который шифрует закрытый ключ.  
  
-   ДЕШИФРОВАНИЕ АСИММЕТРИЧНЫМ ключом: Разрешение CONTROL на ассиметричный ключ и пароль, который шифрует закрытый ключ.  
  
-   DECRYPTION BY PASSWORD: знание одного из паролей, использованного для шифрования симметричного ключа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-opening-a-symmetric-key-by-using-a-certificate"></a>A. Открытие симметричного ключа с помощью сертификата  
 Следующий пример иллюстрирует открытие симметричного ключа `SymKeyMarketing3` и его расшифровку с помощью закрытого ключа сертификата `MarketingCert9`.  
  
```  
USE AdventureWorks2012;  
OPEN SYMMETRIC KEY SymKeyMarketing3   
    DECRYPTION BY CERTIFICATE MarketingCert9;  
GO  
```  
  
### <a name="b-opening-a-symmetric-key-by-using-another-symmetric-key"></a>Б. Открытие симметричного ключа с помощью другого симметричного ключа  
 Следующий пример иллюстрирует открытие симметричного ключа `MarketingKey11` и его расшифровку с помощью симметричного ключа `HarnpadoungsatayaSE3`.  
  
```  
USE AdventureWorks2012;  
-- First open the symmetric key that you want for decryption.  
OPEN SYMMETRIC KEY HarnpadoungsatayaSE3   
    DECRYPTION BY CERTIFICATE sariyaCert01;  
-- Use the key that is already open to decrypt MarketingKey11.  
OPEN SYMMETRIC KEY MarketingKey11   
    DECRYPTION BY SYMMETRIC KEY HarnpadoungsatayaSE3;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  
