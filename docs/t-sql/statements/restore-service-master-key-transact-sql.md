---
title: RESTORE SERVICE MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RESTORE SERVICE MASTER KEY
- RESTORE_SERVICE_MASTER_KEY_TSQL
- LOAD SERVICE MASTER KEY
- LOAD_SERVICE_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- importing Service Master Keys
- copying Service Master Keys
- service master key [SQL Server], importing
- RESTORE SERVICE MASTER KEY statement
- transferring Service Master Keys
ms.assetid: a68fd0ee-70ce-4104-aca0-fcae5f41fc38
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: ee122adb459586f370f2b115f161c56468f4ce7a
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327665"
---
# <a name="restore-service-master-key-transact-sql"></a>Инструкция RESTORE SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Импортирует главный ключ службы из файла резервной копии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE SERVICE MASTER KEY FROM FILE = 'path_to_file'   
    DECRYPTION BY PASSWORD = 'password' [FORCE]  
```  
  
## <a name="arguments"></a>Аргументы  
 FILE **='**_path\_to\_file_**'**  
 Задает полный путь, включающий в себя имя файла, к сохраненному главному ключу службы. *path_to_file* может быть локальным путем или UNC-путем к расположению в сети.  
  
 PASSWORD **='**_password_**'**  
 Задает пароль, необходимый для расшифровки главного ключа службы, импортирующегося из файла.  
  
 FORCE  
 Принудительно заменяет главный ключ службы, несмотря на риск потери данных.  
  
## <a name="remarks"></a>Remarks  
 При восстановлении главного ключа службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расшифровывает все ключи и секретные коды, зашифрованные вместе с текущим главным ключом службы, а затем зашифровывает их вместе с восстановленным ключом из файла резервной копии.  
  
 Если во время расшифровки любого объекта произойдет ошибка, восстановление будет прервано. Чтобы пропускать ошибки, можно использовать параметр FORCE, но это приведет к потере всех данных, которые не удается расшифровать.  
  
> [!CAUTION]  
>  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот ключ явно или неявно защищает все остальные ключи в дереве. Если зависящий от него ключ не может быть расшифрован, но восстановление продолжено, то данные, защищенные этим ключом, будут утеряны.  
  
 Повторное формирование иерархии шифрования — ресурсоемкая операция. Ее нужно назначить на период низкой нагрузки на сервер.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER на сервер.  
  
## <a name="examples"></a>Примеры  
 В следующем примере главный ключ службы восстанавливается из файла резервной копии:  
  
```  
RESTORE SERVICE MASTER KEY   
    FROM FILE = 'c:\temp_backups\keys\service_master_key'   
    DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Главный ключ службы](../../relational-databases/security/encryption/service-master-key.md)   
 [ALTER SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-service-master-key-transact-sql.md)   
 [BACKUP SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
