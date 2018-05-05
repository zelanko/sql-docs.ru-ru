---
title: sp_delete_firewall_rule (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 07/27/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_firewall_rule_TSQL
- sp_delete_firewall_rule
- sys.sp_delete_firewall_rule
- sys.sp_delete_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_firewall_rule procedure
ms.assetid: cf93eed1-ba97-4850-9fcc-b9c5a9317908
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 663bf717182ef19a6d6c175dbf62ad51634c9321
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletefirewallrule-azure-sql-database"></a>sp_delete_firewall_rule (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Удаляет параметры брандмауэра на уровне сервера с локального сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Эта хранимая процедура доступна только в базе данных master для имени входа субъекта серверного уровня.  

  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_delete_firewall_rule [@name =] 'name' 
[ ; ] 
```  
  
## <a name="arguments"></a>Аргументы  
 Аргумент хранимой процедуры:  
  
 [@name =] '*имя*"  
 Имя параметра брандмауэра уровня сервера, который будет удален. *имя* — **nvarchar (128)** без значения по умолчанию.  
  
## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Только имя входа субъекта серверного уровня, созданное в процессе провизионирования, может удалить правила брандмауэра на уровне сервера. Пользователь должен быть подключен к базе данных master для выполнения sp_delete_firewall_rule.  
  
## <a name="example"></a>Пример  
 Следующий пример удаляет параметр брандмауэра уровня сервера с именем «Example setting 1». Выполните инструкцию в виртуальной базы данных master.  
  
```   
EXEC sp_delete_firewall_rule N'Example setting 1';   
```  
  
## <a name="see-also"></a>См. также  
 [Брандмауэр базы данных Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Как: Настройка параметров брандмауэра (база данных Azure SQL)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sys.firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
  
  


