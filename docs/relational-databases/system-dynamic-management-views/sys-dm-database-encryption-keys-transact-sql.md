---
title: sys. dm_database_encryption_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e716c826fd366fda4505b7fcf9ec8e3b756ec25
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80531051"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о состоянии шифрования базы данных и о связанных ключах шифрования базы данных. Дополнительные сведения о шифровании баз данных см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|  
|encryption_state|**int**|Указывает, является ли база данных зашифрованной или незашифрованной.<br /><br /> 0 = нет ключа шифрования базы данных, нет шифрования<br /><br /> 1 = не зашифрована<br /><br /> 2 = выполняется шифрование<br /><br /> 3 = зашифрована<br /><br /> 4 = выполняется изменение ключа<br /><br /> 5 = выполняется расшифровка<br /><br /> 6 = производится изменение защиты (изменился сертификат или асимметричный ключ, которым зашифрован ключ шифрования базы данных).|  
|create_date|**datetime**|Отображает дату (в формате UTC) создания ключа шифрования.|  
|regenerate_date|**datetime**|Отображает дату (в формате UTC) повторного создания ключа шифрования.|  
|modify_date|**datetime**|Отображает дату (в формате UTC) изменения ключа шифрования.|  
|set_date|**datetime**|Отображает дату (в формате UTC) того, что ключ шифрования был применен к базе данных.|  
|opened_date|**datetime**|Показывает время последнего открытия ключа базы данных (в формате UTC).|  
|key_algorithm|**nvarchar(32)**|Отображает алгоритм, используемый для ключа.|  
|key_length|**int**|Отображает длину ключа.|  
|encryptor_thumbprint|**varbinary(20)**|Показывает отпечаток шифратора.|  
|encryptor_type|**nvarchar(32)**|**Применимо к** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (с по [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Описывает шифратор.|  
|percent_complete|**real**|Процент выполнения шифрования базы данных. Значение 0, если изменения состояния не было.|
|encryption_state_desc|**nvarchar(32)**|**Область применения**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] и более поздних версий.<br><br> Строка, указывающая, является ли база данных зашифрованной или не зашифрованной.<br><br>None<br><br>НЕЗАШИФРОВАННЫЕ<br><br>Шифрование<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**Область применения**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] и более поздних версий.<br><br>Указывает текущее состояние сканирования шифрования. <br><br>0 = проверка не инициирована, TDE не включен<br><br>1 = выполняется сканирование.<br><br>2 = Проверка выполняется, но приостановлена, пользователь может возобновить работу.<br><br>3 = сканирование было прервано по какой-то причине, требуется вмешательство вручную. Для получения дополнительной помощи обратитесь в служба поддержки Майкрософт.<br><br>4 = сканирование успешно завершено, TDE включен и шифрование завершено.|
|encryption_scan_state_desc|**nvarchar(32)**|**Область применения**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] и более поздних версий.<br><br>Строка, указывающая текущее состояние сканирования шифрования.<br><br> None<br><br>RUNNING<br><br>SUSPENDED<br><br>ABORTED<br><br>ЗАВЕРШЕНИЯ|
|encryption_scan_modify_date|**datetime**|**Область применения**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] и более поздних версий.<br><br> Отображает дату (в формате UTC) последнего изменения состояния проверки шифрования.|
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="see-also"></a>См. также:  

 [Динамические административные представления и функции, связанные с безопасностью &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Прозрачное шифрование данных &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server и ключи шифрования базы данных &#40;ядро СУБД&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Параметры ALTER DATABASE SET &#40;&#41;Transact-SQL](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Создание ключа шифрования базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [&#40;&#41;Transact-SQL в инструкции ALTER DATABASE ENCRYPTION KEY](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
