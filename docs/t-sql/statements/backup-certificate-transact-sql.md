---
title: "СЕРТИФИКАТА резервной копии (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: fb1632ed04904150247280962d8423a493b51d60
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Экспортирует сертификат в файл.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>Аргументы  
 *путь_к_файлу*  
 Указывает полный путь, включая имя файла, для файла, в котором должен быть сохранен сертификат. Это может быть локальный путь или UNC-путь к местоположению в сети. По умолчанию задается путь к папке DATA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *path_to_private_key_file*  
 Указывает полный путь, включая имя файла, для файла, в котором должен быть сохранен закрытый ключ. Это может быть локальный путь или UNC-путь к местоположению в сети. По умолчанию задается путь к папке DATA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *encryption_password*  
 Пароль, используемый для шифрования закрытого ключа перед записью ключа в файл резервной копии. Пароль проходит проверку сложности.  
  
 *decryption_password*  
 Пароль, используемый для дешифрования закрытого ключа перед созданием резервной копии ключа.  
  
## <a name="remarks"></a>Замечания  
 Если закрытый ключ зашифрован с паролем в базе данных, необходимо указать пароль для дешифрования.  
  
 При создании резервной копии закрытого ключа в файле шифрование является необходимым. Пароль, используемый для защиты резервной копии сертификата, не является тем же ключом, который применялся для шифрования закрытого ключа сертификата.  
  
 Для восстановления резервной копии сертификата, использовать [CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md)инструкции.  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL для сертификата и знание пароля, использованного для шифрования закрытого ключа. Если только общедоступная часть сертификата была подвергнута резервному копированию, требуются некоторые разрешения для сертификата, и чтобы для вызывающей программы не было запрещено разрешение VIEW для сертификата.  
  
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
 [ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [УДАЛИТЬ СЕРТИФИКАТ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)  
  
  


