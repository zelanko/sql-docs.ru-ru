---
title: sp_syscollector_set_warehouse_instance_name (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_warehouse_instance_name_TSQL
- sp_syscollector_set_warehouse_instance_name
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_warehouse_instance_name
ms.assetid: 5320fcd4-bed1-468f-b784-a5e10fcfaeb6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 60208e714595338e68f0d1946cc2e767df45e409
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769682"
---
# <a name="sp_syscollector_set_warehouse_instance_name-transact-sql"></a>sp_syscollector_set_warehouse_instance_name (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Задает имя экземпляра для строки подключения, которая используется для подключения к хранилищу данных управления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_set_warehouse_instance_name [ @instance_name = ] 'instance_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @instance_name =] "*instance_name*"  
 Имя экземпляра. Аргумент *instance_name* имеет тип **sysname** и значение по умолчанию для локального экземпляра при значении NULL.  
  
> **Примечание.**_instance_name_ должно быть полным именем экземпляра, состоящим из имени компьютера и имени экземпляра в формате *ComputerName* \\ *имя_экземпляра*.    
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Необходимо отключить сборщик данных перед изменением конфигурации на уровне сборщика данных. Если включен сборщик данных, эта процедура завершится с ошибкой.  
  
 Чтобы просмотреть текущее имя экземпляра, запросите [syscollector_config_store](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md) системное представление.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется настройка сборщика данных для использования экземпляра хранилища управляющих данных на удаленном сервере. Здесь удаленный сервер имеет имя `RemoteSERVER`, а база данных установлена в экземпляре по умолчанию.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_set_warehouse_instance_name N'RemoteSERVER'; -- the default instance is assumed on the remote server  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_config_store (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)  
  
  
