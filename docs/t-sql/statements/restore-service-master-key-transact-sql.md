---
title: "RESTORE SERVICE MASTER KEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f88ab43c6e452bbbb3b6cfa32e858ee1f091e366
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
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
 ФАЙЛ **= "***путь_к_файлу***"**  
 Задает полный путь, включающий в себя имя файла, к сохраненному главному ключу службы. *путь_к_файлу* может быть локальным путем или UNC-путь в сетевую папку.  
  
 ПАРОЛЬ **= "***пароль***"**  
 Задает пароль, необходимый для расшифровки главного ключа службы, импортирующегося из файла.  
  
 FORCE  
 Принудительно заменяет главный ключ службы, несмотря на риск потери данных.  
  
## <a name="remarks"></a>Замечания  
 При восстановлении главного ключа службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расшифровывает все ключи и секретные коды, зашифрованные вместе с текущим главным ключом службы, а затем зашифровывает их вместе с восстановленным ключом из файла резервной копии.  
  
 Если во время расшифровки любого объекта произойдет ошибка, восстановление будет прервано. Чтобы пропускать ошибки, можно использовать параметр FORCE, но это приведет к потере всех данных, которые не удается расшифровать.  
  
> [!CAUTION]  
>  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот ключ явно или неявно защищает все остальные ключи в дереве. Если зависящий от него ключ не может быть расшифрован, но восстановление продолжено, то данные, защищенные этим ключом, будут утеряны.  
  
 Повторное формирование иерархии шифрования — ресурсоемкая операция. Ее нужно назначить на период низкой нагрузки на сервер.  
  
## <a name="permissions"></a>Permissions  
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
 [ALTER SERVICE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-master-key-transact-sql.md)   
 [Резервная копия главного ключа службы &#40; Transact-SQL &#41;](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
