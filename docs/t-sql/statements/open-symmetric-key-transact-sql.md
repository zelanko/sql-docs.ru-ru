---
title: OPEN SYMMETRIC KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 123689fada7686f68b7dce614198452355876d12
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790085"
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
  
 CERTIFICATE *certificate_name*  
 Имя сертификата, закрытый ключ которого будет использоваться для расшифровки симметричного ключа.  
  
 ASYMMETRIC KEY *asym_key_name*  
 Имя асимметричного ключа, закрытый ключ которого будет использоваться для расшифровки симметричного ключа.  
  
 WITH PASSWORD ='*password*'  
 Пароль, который использовался для шифрования закрытого ключа сертификата или асимметричного ключа.  
  
 SYMMETRIC KEY *decrypting_key_name*  
 Имя симметричного ключа, который будет использоваться для расшифровки открываемого симметричного ключа.  
  
 PASSWORD ='*password*'  
 Пароль, использовавшийся для защиты симметричного ключа.  
  
## <a name="remarks"></a>Примечания  
 Открытые симметричные ключи привязаны к сеансу, а не к контексту безопасности. Открытый ключ останется доступным, пока не будет явно закрыт или сеанс не будет прерван. Если открыт симметричный ключ, после чего произошло переключение контекста, ключ останется открытым и будет доступным в олицетворенном контексте. Сведения о симметричных ключах доступны в представлении каталога [sys.openkeys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md).  
  
 Если симметричный ключ был зашифрован другим ключом, сначала необходимо открыть этот ключ.  
  
 Если симметричный ключ уже открыт, то запрос является запросом **NO_OP**.  
  
 Если пароль, сертификат или ключ для расшифровки симметричного ключа неверен, запрос завершается сбоем.  
  
 Симметричные ключи, созданные из поставщиков шифрования, не могут быть открыты. Операции шифрования и расшифровки, для которых используется симметричный ключ этого типа, выполняются успешно без инструкции **OPEN**, поскольку открытие и закрытие ключа осуществляется поставщиком шифрования.  
  
## <a name="permissions"></a>Разрешения  
 Участник должен обладать некоторыми разрешениями на ключ и не должен иметь запрета на разрешение VIEW DEFINITION для ключа. Дополнительные требования зависят от механизма расшифровки:  
  
-   DECRYPTION BY CERTIFICATE: разрешение CONTROL на сертификат и пароль, который шифрует закрытый ключ сертификата;  
  
-   DECRYPTION BY ASYMMETRIC KEY: разрешение CONTROL на асимметричный ключ и знание пароля, который шифрует закрытый ключ сертификата;  
  
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
  
## <a name="see-also"></a>См. также  
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  
