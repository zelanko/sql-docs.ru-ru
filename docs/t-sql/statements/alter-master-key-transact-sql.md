---
title: "ALTER MASTER KEY (Transact-SQL) | Документы Microsoft"
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
- ALTER MASTER KEY
- ALTER_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- ALTER MASTER KEY statement
- decryption [SQL Server], Database Master Key
- FORCE option
- encryption [SQL Server], Database Master Key
- database master key [SQL Server], modifying
- cryptography [SQL Server], Database Master Key
- modifying Database Master Key
- service master key [SQL Server], modifying
- DROP ENCRYPTION BY SERVICE MASTER KEY phrase
ms.assetid: 8ac501c3-4280-4d5b-b58a-1524fa715b50
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 638449f85daf7b13abc37c5750eb32ec5603d7ef
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-master-key-transact-sql"></a>ALTER MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Изменяет свойства главного ключа базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'  
  
<encryption_option> ::=  
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
    |   
    DROP ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
```  
```  
-- Syntax for Azure SQL Database
-- Note: DROP ENCRYPTION BY SERVICE MASTER KEY is not supported on Azure SQL Database.
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'  
  
<encryption_option> ::=  
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
    |   
    DROP ENCRYPTION BY { PASSWORD = 'password' }  
```  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD ='password'<encryption_option> ::=  
    ADD ENCRYPTION BY SERVICE MASTER KEY   
    |   
    DROP ENCRYPTION BY SERVICE MASTER KEY  
```  
  
## <a name="arguments"></a>Аргументы  
 ПАРОЛЬ = "*пароль*"  
 Указывает пароль, используемый для шифрования или расшифровки главного ключа базы данных. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Замечания  
 С аргументом REGENERATE главный ключ базы данных и все защищаемые им ключи создаются повторно. Ключи сначала расшифровываются с помощью старого главного ключа, а затем шифруются с помощью нового. Данная ресурсоемкая операция должна быть назначена на период низкой загрузки, за исключением случаев, когда главный ключ был скомпрометирован.  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] использует для защиты главного ключа службы и главного ключа базы данных алгоритм шифрования AES. AES - это новый алгоритм шифрования, отличный от алгоритма 3DES, используемого в более ранних версиях. После обновления экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] необходимо заново сформировать главный ключ службы и главный ключ базы данных, чтобы обновить главные ключи до алгоритма AES. Дополнительные сведения о повторном создании главного ключа службы см. в разделе [ALTER SERVICE MASTER KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-service-master-key-transact-sql.md).  
  
 Если используется аргумент FORCE, повторное создание ключей продолжается даже в случае, если главный ключ недоступен или сервер не может расшифровать все зашифрованные закрытые ключи. Если главный ключ не может быть открыт, используйте [RESTORE MASTER KEY](../../t-sql/statements/restore-master-key-transact-sql.md) инструкцию, чтобы восстановить главный ключ из резервной копии. Аргумент FORCE следует использовать только в случае, если главный ключ получить невозможно или, при неудачной попытке расшифровки Данные, зашифрованные только недоступным ключом, будут потеряны.  
  
 Фраза DROP ENCRYPTION BY SERVICE MASTER KEY позволяет отменить шифрование главного ключа базы данных с помощью главного ключа службы.  
  
 Фраза ADD ENCRYPTION BY SERVICE MASTER KEY приводит к шифрованию копии главного ключа с помощью главного ключа службы, которая затем сохраняется как в текущей базе данных, так и в базе данных master.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL для базы данных. Если главный ключ базы данных зашифрован с паролем, требуется также знание этого пароля.  
  
## <a name="examples"></a>Примеры  
 На этом примере показано, как создается новый главный ключ базы данных `AdventureWorks`, после чего повторно шифруются ключи, стоящие внизу в иерархии шифрования.  
  
```  
USE AdventureWorks2012;  
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере создается новый главный ключ базы данных для `AdventureWorksPDW2012` и повторно шифрует ключи ниже в иерархии шифрования.  
  
```  
USE master;  
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ОТКРЫТЬ ГЛАВНЫЙ ключ &#40; Transact-SQL &#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-master-key-transact-sql.md)   
 [BACKUP MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/backup-master-key-transact-sql.md)   
 [ВОССТАНОВЛЕНИЕ главного ключа &#40; Transact-SQL &#41;](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [DROP MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  


