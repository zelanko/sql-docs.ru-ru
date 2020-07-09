---
title: BACKUP SERVICE MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BACKUP SERVICE MASTER KEY
- DUMP_SERVICE_MASTER_KEY_TSQL
- DUMP SERVICE MASTER KEY
- BACKUP_SERVICE_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backing up service master keys [SQL Server]
- BACKUP SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- exporting Service Master Keys
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], exporting
ms.assetid: f8356683-6680-4f1c-9eaf-5c29a9a9020d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23c401f4af8785518d57c40a3bd0d54c6e89c99f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895533"
---
# <a name="backup-service-master-key-transact-sql"></a>BACKUP SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Экспорт главного ключа службы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BACKUP SERVICE MASTER KEY TO FILE = 'path_to_file'   
    ENCRYPTION BY PASSWORD = 'password'  
```  
  
## <a name="arguments"></a>Аргументы  
 FILE **='***path_to_file***'**  
 Указывает полный путь (включая имя файла) к файлу, в который будет выполнен экспорт главного ключа службы. Это может быть локальный путь или UNC-путь к сетевой папке.  
  
 PASSWORD **='***password***'**  
 Пароль, используемый для шифрования главного ключа службы в файле резервной копии. Пароль проходит проверку сложности. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).  
  
## <a name="remarks"></a>Remarks  
 Необходимо создавать резервные копии главного ключа службы и хранить их в безопасном удаленном месте. Создание такой резервной копии должно быть одной из первых задач администрирования, выполненных на сервере.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER на сервер.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается файл резервной копии главного ключа службы.  
  
```  
BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_key' ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-service-master-key-transact-sql.md)   
 [RESTORE SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
  
