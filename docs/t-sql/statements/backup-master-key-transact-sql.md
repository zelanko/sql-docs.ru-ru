---
description: BACKUP MASTER KEY (Transact-SQL)
title: BACKUP MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BACKUP MASTER KEY
- DUMP_MASTER_KEY_TSQL
- BACKUP_MASTER_KEY_TSQL
- DUMP MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- BACKUP MASTER KEY statement
- exporting Database Master Keys
- encryption [SQL Server], Database Master Key
- cryptography [SQL Server], Database Master Key
- backing up master keys [SQL Server]
- database master key [SQL Server], exporting
ms.assetid: 0e25fe22-2536-4d7e-ba4a-1921e880f367
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8c7d0bd39ebda34677469a45687fd78f0e4124cc
ms.sourcegitcommit: ac9feb0b10847b369b77f3c03f8200c86ee4f4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2020
ms.locfileid: "90688559"
---
# <a name="backup-master-key-transact-sql"></a>BACKUP MASTER KEY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Выполняет экспорт главного ключа базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
BACKUP MASTER KEY TO FILE = 'path_to_file'   
    ENCRYPTION BY PASSWORD = 'password'  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 FILE ='*path_to_file*'  
 Указывает полный путь и имя файла, в который экспортируется главный ключ базы данных. Это может быть локальный путь или UNC-путь к сетевой папке.  
  
 PASSWORD ='*password*'  
 Пароль, используемый для шифрования главного ключа базы данных в файле. Пароль проходит проверку сложности. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).  
  
## <a name="remarks"></a>Комментарии  
 Главный ключ должен быть открыт и, таким образом, расшифрован, прежде чем производится его резервное копирование. Если он зашифрован главным ключом службы, то его не нужно открывать явным образом. Но если главный ключ зашифрован только паролем, его явное открытие обязательно.  
  
 Рекомендуется создать резервную копию главного ключа сразу же после его создания и затем сохранить в надежном месте.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится создание резервной копии главного ключа базы данных `AdventureWorks2012`. Поскольку главный ключ не зашифрован главным ключом службы, для его открытия необходимо указать пароль.  
  
```sql  
USE AdventureWorks2012;  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';  
BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
    ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';  
GO   
```  
  
## <a name="see-also"></a>См. также  
 [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md)   
 [OPEN MASTER KEY (Transact-SQL)](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY (Transact-SQL)](../../t-sql/statements/close-master-key-transact-sql.md)   
 [RESTORE MASTER KEY (Transact-SQL)](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY (Transact-SQL)](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
