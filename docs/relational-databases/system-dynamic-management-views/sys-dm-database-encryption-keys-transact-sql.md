---
title: sys.dm_database_encryption_keys (Трансакт-СЗЛ) Документы Майкрософт
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
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531051"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о состоянии шифрования базы данных и о связанных ключах шифрования базы данных. Дополнительные сведения о шифровании баз данных см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|Идентификатор базы данных.|  
|encryption_state|**Int**|Указывает, является ли база данных зашифрованной или незашифрованной.<br /><br /> 0 = нет ключа шифрования базы данных, нет шифрования<br /><br /> 1 = не зашифрована<br /><br /> 2 = выполняется шифрование<br /><br /> 3 = зашифрована<br /><br /> 4 = выполняется изменение ключа<br /><br /> 5 = выполняется расшифровка<br /><br /> 6 = производится изменение защиты (изменился сертификат или асимметричный ключ, которым зашифрован ключ шифрования базы данных).|  
|create_date|**Datetime**|Отображает дату (в UTC) ключ шифрования был создан.|  
|regenerate_date|**Datetime**|Отображает дату (в UTC) ключ шифрования был регенерирован.|  
|modify_date|**Datetime**|Отображает дату (в UTC) ключ шифрования был изменен.|  
|set_date|**Datetime**|Отображает дату (в UTC) ключ шифрования был применен к базе данных.|  
|opened_date|**Datetime**|Показывает, когда (в UTC) ключ базы данных был в последний раз открыт.|  
|key_algorithm|**nvarchar(32)**|Отображает алгоритм, используемый для ключа.|  
|key_length|**Int**|Отображает длину ключа.|  
|encryptor_thumbprint|**varbinary(20)**|Показывает отпечаток шифратора.|  
|encryptor_type|**nvarchar(32)**|**Применяется**к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : (через [текущую версию](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Описывает шифратор.|  
|percent_complete|**real**|Процент выполнения шифрования базы данных. Значение 0, если изменения состояния не было.|
|encryption_state_desc|**nvarchar(32)**|**Применяется**к [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : и позже.<br><br> Строка, которая указывает, является ли база данных зашифрована или не зашифрована.<br><br>None<br><br>Незашифрованные<br><br>Зашифрованные<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**Int**|**Применяется**к [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : и позже.<br><br>Указывает текущее состояние сканирования шифрования. <br><br>0 - Сканирование не было инициировано, TDE не включено<br><br>1 - Завершено сканирование.<br><br>2 - Сканирование продолжается, но было приостановлено, пользователь может возобновить.<br><br>3 - Сканирование было прервано по какой-то причине, требуется ручное вмешательство. Для получения дополнительной помощи обратитесь в службу поддержки корпорации Майкрософт.<br><br>4 - Сканирование было успешно завершено, TDE включен освоено, а шифрование завершено.|
|encryption_scan_state_desc|**nvarchar(32)**|**Применяется**к [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : и позже.<br><br>Строка, указывающая текущее состояние сканирования шифрования.<br><br> None<br><br>RUNNING<br><br>SUSPENDED<br><br>ABORTED<br><br>Полный|
|encryption_scan_modify_date|**Datetime**|**Применяется**к [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] : и позже.<br><br> Отображает дату (в UTC) состояние сканирования шифрования последнее изменение.|
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], `VIEW SERVER STATE` требуется разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium Tiers `VIEW DATABASE STATE` требуется разрешение в базе данных. В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] стандартных и базовых уровнях требуется **администратор сервера** или учетная запись **администратора активного каталога Azure.**   

## <a name="see-also"></a>См. также:  

 [Представления и функции динамического управления, связанные с безопасностью, &#40;&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Прозрачное шифрование данных &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Шифрование серверов S'L](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [S'L Сервер и базы данных шифрования ключи &#40;базы данных&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ОПЦИоны ALTER DATABASE SET &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
