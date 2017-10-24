---
title: "ALTER CERTIFICATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_CERTIFICATE_TSQL
- ALTER CERTIFICATE
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- encryption [SQL Server], certificates
- modifying certificates
- private keys [SQL Server]
- ALTER CERTIFICATE statement
- certificates [SQL Server], modifying
ms.assetid: da4dc25e-72e0-4036-87ce-22de83160836
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: da51e41cc5adf4fa9f4f57cfe094fe5a72119c70
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет закрытый ключ, используемый для шифрования сертификата, или добавляет закрытый ключ, если он не существует. Изменяет доступность сертификата для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER CERTIFICATE certificate_name   
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY ( <private_key_spec> [ ,... ] )  
    | WITH ACTIVE FOR BEGIN_DIALOG = [ ON | OFF ]  
  
<private_key_spec> ::=   
      FILE = 'path_to_private_key'   
    | DECRYPTION BY PASSWORD = 'key_password'   
    | ENCRYPTION BY PASSWORD = 'password'   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_сертификата*  
 Уникальное имя, под которым сертификат известен в базе данных.  
  
 ФАЙЛ **= "***path_to_private_key***"**  
 Указывает полный путь к закрытому ключу, включая имя файла. Этот аргумент может быть локальным путем или UNC-путем к точке в сети. Доступ к файлу осуществляется в контексте безопасности учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используя этот аргумент, необходимо убедиться в том, что учетная запись службы имеет доступ к указанному файлу.  
  
 ПАРОЛЬ дешифрования УКАЗЫВАТЬ **= "***key_password***"**  
 Указывает пароль, необходимый для расшифровки закрытого ключа.  
  
 ENCRYPTION BY PASSWORD **= "***пароль***"**  
 Задает пароль, который используется для шифрования закрытого ключа сертификата в базе данных. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Password Policy](../../relational-databases/security/password-policy.md).  
  
 REMOVE PRIVATE KEY  
 Указывает, что закрытый ключ больше не нужно хранить в базе данных.  
  
 ACTIVE FOR BEGIN_DIALOG  **=**  {ON | {OFF}  
 Делает сертификат доступным для инициатора диалога с компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="remarks"></a>Замечания  
 Закрытый ключ должен соответствовать открытый ключ, заданный *имя_сертификата*.  
  
 Предложение DECRYPTION BY PASSWORD может быть опущено, если пароль в файле защищен паролем, равным NULL.  
  
 Если закрытый ключ сертификата, уже существующий в базе данных, импортируется из файла, закрытый ключ будет автоматически защищен главным ключом базы данных. Чтобы защитить закрытый ключ паролем, используйте предложение ENCRYPTION BY PASSWORD.  
  
 Параметр REMOVE PRIVATE KEY удалит закрытый ключ сертификата из базы данных. Это можно сделать, если сертификат будет использоваться для проверки подписей или в сценариях компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], не требующих закрытого ключа. Не удаляйте закрытый ключ сертификата, который защищает симметричный ключ.  
  
 Указывать пароль расшифровки не нужно, если закрытый ключ зашифрован с помощью главного ключа базы данных.  
  
> [!IMPORTANT]  
>  Всегда создавайте архивную копию закрытого ключа, прежде чем удалять его из базы данных. Дополнительные сведения см. в разделе [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md).  
  
 Параметр WITH PRIVATE KEY недоступен в автономной базе данных.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения ALTER для сертификата.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-password-of-a-certificate"></a>A. Изменение пароля сертификата  
  
```  
ALTER CERTIFICATE Shipping04   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = 'pGF$5DGvbd2439587y',  
    ENCRYPTION BY PASSWORD = '4-329578thlkajdshglXCSgf');  
GO  
```  
  
### <a name="b-changing-the-password-that-is-used-to-encrypt-the-private-key"></a>Б. Изменение пароля, используемого для шифрования закрытого ключа  
  
```  
ALTER CERTIFICATE Shipping11   
    WITH PRIVATE KEY (ENCRYPTION BY PASSWORD = '34958tosdgfkh##38',  
    DECRYPTION BY PASSWORD = '95hkjdskghFDGGG4%');  
GO  
```  
  
### <a name="c-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>В. Импорт закрытого ключа для сертификата, который уже присутствует в базе данных  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = 'c:\\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
### <a name="d-changing-the-protection-of-the-private-key-from-a-password-to-the-database-master-key"></a>Г. Изменение защиты закрытого ключа паролем на защиту главным ключом базы данных  
  
```  
ALTER CERTIFICATE Shipping15   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = '95hk000eEnvjkjy#F%');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [УДАЛИТЬ СЕРТИФИКАТ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


