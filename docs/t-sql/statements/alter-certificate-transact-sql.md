---
title: ALTER CERTIFICATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/18/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bba8adc043d5fa98f1d9c1773952f6366518823b
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54326705"
---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

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
-- Syntax for Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *certificate_name*  
 Уникальное имя, под которым сертификат известен в базе данных.  
  
 FILE **='**_path\_to\_private\_key_**'**  
 Указывает полный путь к закрытому ключу, включая имя файла. Этот аргумент может быть локальным путем или UNC-путем к точке в сети. Доступ к файлу осуществляется в контексте безопасности учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используя этот аргумент, необходимо убедиться в том, что учетная запись службы имеет доступ к указанному файлу.  
  
 DECRYPTION BY PASSWORD **='**_key\_password_**'**  
 Указывает пароль, необходимый для расшифровки закрытого ключа.  
  
 ENCRYPTION BY PASSWORD **='**_password_**'**  
 Задает пароль, который используется для шифрования закрытого ключа сертификата в базе данных. *password* должен соответствовать требованиям политики паролей Windows применительно к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).  
  
 REMOVE PRIVATE KEY  
 Указывает, что закрытый ключ больше не нужно хранить в базе данных.  
  
 ACTIVE FOR BEGIN_DIALOG **=** { ON | OFF }  
 Делает сертификат доступным для инициатора диалога с компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="remarks"></a>Примечания  
 Закрытый ключ должен соответствовать открытому ключу, заданному аргументом *certificate_name*.  
  
 Предложение DECRYPTION BY PASSWORD может быть опущено, если пароль в файле защищен паролем, равным NULL.  
  
 Если закрытый ключ сертификата, уже существующий в базе данных, импортируется из файла, закрытый ключ будет автоматически защищен главным ключом базы данных. Чтобы защитить закрытый ключ паролем, используйте предложение ENCRYPTION BY PASSWORD.  
  
 Параметр REMOVE PRIVATE KEY удалит закрытый ключ сертификата из базы данных. Это можно сделать, если сертификат будет использоваться для проверки подписей или в сценариях компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], не требующих закрытого ключа. Не удаляйте закрытый ключ сертификата, который защищает симметричный ключ.  
  
 Указывать пароль расшифровки не нужно, если закрытый ключ зашифрован с помощью главного ключа базы данных.  
  
> [!IMPORTANT]  
>  Всегда создавайте архивную копию закрытого ключа, прежде чем удалять его из базы данных. Дополнительные сведения см. в разделе [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md).  
  
 Параметр WITH PRIVATE KEY недоступен в автономной базе данных.  
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="see-also"></a>См. также  
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

