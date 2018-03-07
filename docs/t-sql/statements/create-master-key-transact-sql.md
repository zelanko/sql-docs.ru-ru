---
title: "СОЗДАЙТЕ ГЛАВНЫЙ ключ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MASTER_KEY_TSQL
- MASTER_KEY_TSQL
- MASTER KEY
- CREATE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- database master key [SQL Server]
- CREATE MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- database master key [SQL Server], creating
ms.assetid: 1710a305-1a4f-48ec-836c-11ffd0356d76
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aaec4d28dc95d792faa6406ef68df50167d0f091
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="create-master-key-transact-sql"></a>CREATE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Создает главный ключ базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Parallel Data Warehouse  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password'  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE MASTER KEY [ ENCRYPTION BY PASSWORD ='password' ]
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 ПАРОЛЬ = "*пароль*"  
 Пароль, который использовался при шифровке главного ключа базы данных. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *пароль* является необязательным в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].  
  
## <a name="remarks"></a>Замечания  
 Главный ключ базы данных — это симметричный ключ, который применяется для защиты закрытых ключей сертификатов и асимметричный ключей, которые есть в базе данных. При создании этот главный ключ зашифровывается с помощью алгоритма AES_256 и предоставленного пользователем пароля. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] используется алгоритм Triple DES. Чтобы обеспечить возможность автоматического расшифровывания главного ключа, его копия шифруется с помощью главного ключа службы и хранится в текущей базе данных и базе данных master. Как правило, копия, которая хранится в базе данных master, обновляется без взаимодействия с пользователем при каждом изменении главного ключа. Это значение по умолчанию можно изменить с помощью параметра DROP ENCRYPTION BY SERVICE MASTER KEY [ALTER MASTER KEY](../../t-sql/statements/alter-master-key-transact-sql.md). Главный ключ, который не зашифрован с помощью главного ключа службы, следует открывать с помощью [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) инструкции и пароля.  
  
 Столбец is_master_key_encrypted_by_server в представлении каталога sys.databases базы данных master показывает, зашифрован ли главный ключ базы данных с помощью главного ключа службы.  
  
 Сведения о главном ключе базы данных доступны в представлении каталога sys.symmetric_keys.  

Для SQL Server и параллельных хранилищ данных главный ключ защищен обычно главного ключа службы и по крайней мере один пароль. В случае базы данных, физически переносится на другой сервер (доставка журналов, восстановление резервной копии, т. д.) база данных будет содержать копию главного ключа, зашифрованная исходном сервере главный ключ службы (если такое шифрование явным образом удален с помощью ALTER MASTER KEY DDL) и его копии, зашифрованный при помощи каждого пароля, указанное во время СОЗДАНИЯ главного ключа или последующие операции DDL ALTER MASTER KEY. Чтобы восстановить главный ключ и все данные, зашифрованные с помощью главного ключа, который является корнем иерархии ключа после перемещения базы данных, пользователь должен будет использовать инструкции OPEN MASTER KEY, используя один пароль, используемый для защиты главного ключа , восстановить резервную копию главного ключа или восстановление резервной копии из исходной главного ключа службы на новом сервере. 

Для [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], защита паролем не рассматривается как механизм безопасности, чтобы предотвратить потерю данных в случае в ситуациях, где базы данных перемещаются с одного сервера на другой, как защита главным ключом службы, на главный ключ Управляет платформы Microsoft Azure. Таким образом, пароль ключа мазерный является необязательным в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].
  
> [!IMPORTANT]  
>  Резервную копию главного ключа с помощью [резервную КОПИЮ главного ключа](../../t-sql/statements/backup-master-key-transact-sql.md) и хранить ее в надежном месте.  
  
 Главный ключ службы и главный ключ базы данных защищаются алгоритмом шифрования AES-256.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается главный ключ базы данных в текущей базе данных. Ключ зашифрован с помощью пароля `23987hxJ#KL95234nl0zBe`.  
  
```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
GO  
```  

  
## <a name="see-also"></a>См. также:  
 [sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [ОТКРЫТЬ ГЛАВНЫЙ ключ &#40; Transact-SQL &#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-master-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  


