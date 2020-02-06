---
title: BACKUP CERTIFICATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DUMP_CERTIFICATE_TSQL
- BACKUP CERTIFICATE
- sql13.swb.exportcertificate.f1
- DUMP CERTIFICATE
- BACKUP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- decryption [SQL Server], certificates
- exporting certificates
- certificates [SQL Server], exporting
- BACKUP CERTIFICATE statement
- backing up certificates [SQL Server]
- decryption [SQL Server]
- cryptography [SQL Server], certificates
ms.assetid: 509b9462-819b-4c45-baae-3d2d90d14a1c
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7b2559ca1eee0f2787fbf74adba97b03671d6faf
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68091762"
---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Экспортирует сертификат в файл.  
  
 ![Значок ссылки](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
BACKUP CERTIFICATE certname TO FILE = 'path_to_file'  
    [ WITH PRIVATE KEY   
      (   
        FILE = 'path_to_private_key_file' ,  
        ENCRYPTION BY PASSWORD = 'encryption_password'   
        [ , DECRYPTION BY PASSWORD = 'decryption_password' ]   
      )   
    ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>Аргументы  
 *certname*  
 Имя копируемого сертификата.

 TO FILE = '*путь к файлу*'  
 Указывает полный путь, включая имя файла, для файла, в котором должен быть сохранен сертификат. Это может быть локальный путь или UNC-путь к расположению в сети. Если указано только имя файла, файл будет сохранен в папке данных пользователя по умолчанию для экземпляра (это может быть, а может и не быть папка данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). В SQL Server Express LocalDB папкой данных пользователя по умолчанию для экземпляра является путь, указанный в переменной среды `%USERPROFILE%` учетной записи, создавшей этот экземпляр.  

 WITH PRIVATE KEY указывает, что закрытый ключ сертификата следует сохранить в файл. Это предложение является необязательным.

 FILE = '*путь к файлу закрытого ключа*'  
 Указывает полный путь, включая имя файла, для файла, в котором должен быть сохранен закрытый ключ. Это может быть локальный путь или UNC-путь к расположению в сети. Если указано только имя файла, файл будет сохранен в папке данных пользователя по умолчанию для экземпляра (это может быть, а может и не быть папка данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). В SQL Server Express LocalDB папкой данных пользователя по умолчанию для экземпляра является путь, указанный в переменной среды `%USERPROFILE%` учетной записи, создавшей этот экземпляр.  

 ENCRYPTION BY PASSWORD = '*пароль шифрования*'  
 Пароль, используемый для шифрования закрытого ключа перед записью ключа в файл резервной копии. Пароль проходит проверку сложности.  
  
 DECRYPTION BY PASSWORD = '*пароль шифрования*'  
 Пароль, используемый для дешифрования закрытого ключа перед созданием резервной копии ключа. Этот аргумент не является обязательным, если сертификат зашифрован главным ключом. 
  
## <a name="remarks"></a>Remarks  
 Если закрытый ключ зашифрован с паролем в базе данных, необходимо указать пароль для дешифрования.  
  
 При создании резервной копии закрытого ключа в файле шифрование является необходимым. Пароль, используемый для защиты закрытого ключа в файле, не является тем же ключом, который применялся для шифрования закрытого ключа сертификата в базе данных.  

 Закрытые ключи сохраняются в формате PVK.

 Чтобы восстановить резервную копию сертификата без закрытого ключа или с ним, используйте инструкцию [CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md).
 
 Чтобы восстановить закрытый ключ в существующем сертификате в базе данных, используйте инструкцию [ALTER CERTIFICATE](../../t-sql/statements/alter-certificate-transact-sql.md).
 
 При резервном копировании файлы будут перечислены в учетной записи службы экземпляра SQL Server. Если вам нужно восстановить сертификат сервера, работающего в другой учетной записи, настройте разрешения для файлов, чтобы они считывались новой учетной записью. 
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL для сертификата и знание пароля, использованного для шифрования закрытого ключа. Если резервное копирование выполняется только для общедоступной части сертификата, этой команде требуются некоторые разрешения для сертификата, и чтобы для вызывающей программы не было запрещено разрешение VIEW для сертификата.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-exporting-a-certificate-to-a-file"></a>A. Экспорт сертификата в файл  
 В следующем примере сертификат экспортируется в файл.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert';  
GO  
```  
  
### <a name="b-exporting-a-certificate-and-a-private-key"></a>Б. Экспорт сертификата и закрытого ключа  
 В следующем примере закрытый ключ сертификата, подвергаемого резервному копированию, будет зашифрован с паролем `997jkhUbhk$w4ez0876hKHJH5gh`.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = 'c:\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
### <a name="c-exporting-a-certificate-that-has-an-encrypted-private-key"></a>В. Экспорт сертификата с зашифрованным закрытым ключом  
 В следующем примере закрытый ключ сертификата подвергается шифрованию в базе данных. Дешифрование ключа должно проводиться с паролем `9875t6#6rfid7vble7r`. При сохранении сертификата в файле резервной копии закрытый ключ будет зашифрован с паролем `9n34khUbhk$w4ecJH5gh`.  
  
```  
BACKUP CERTIFICATE sales09 TO FILE = 'c:\storedcerts\sales09cert'   
    WITH PRIVATE KEY ( DECRYPTION BY PASSWORD = '9875t6#6rfid7vble7r' ,  
    FILE = 'c:\storedkeys\sales09key' ,   
    ENCRYPTION BY PASSWORD = '9n34khUbhk$w4ecJH5gh' );  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)  
 [CERTENCODED (Transact-SQL)](../../t-sql/functions/certencoded-transact-sql.md)  
 [CERTPRIVATEKEY (Transact-SQL)](../../t-sql/functions/certprivatekey-transact-sql.md)  
 [CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md)  
 [CERTPROPERTY (Transact-SQL)](../../t-sql/functions/certproperty-transact-sql.md)  
  
  

