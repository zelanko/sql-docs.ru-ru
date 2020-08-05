---
title: sp_delete_firewall_rule
titleSuffix: Azure SQL Database
ms.date: 07/27/2016
ms.service: sql-database
ms.reviewer: ''
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
author: VanMSFT
ms.author: vanto
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 41f4e779ccbab41557cb9ba20b5aa02c65e45919
ms.sourcegitcommit: bc10ec0be5ddfc5f0bc220a9ac36c77dd6b80f1d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544417"
---
# <a name="sp_delete_firewall_rule-azure-sql-database"></a>sp_delete_firewall_rule (база данных SQL Azure)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  Удаляет параметры брандмауэра на уровне сервера с локального сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Эта хранимая процедура доступна только в базе данных master для имени входа субъекта серверного уровня.  

  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_delete_firewall_rule [@name =] 'name' 
[ ; ] 
```  
  
## <a name="arguments"></a>Аргументы  
 Аргумент хранимой процедуры:  
  
 [ @name =] "*имя*"  
 Имя параметра брандмауэра уровня сервера, который будет удален. *Name* имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
## <a name="remarks"></a>Remarks  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Только имя входа субъекта серверного уровня, созданное в процессе провизионирования, может удалить правила брандмауэра на уровне сервера. Для выполнения sp_delete_firewall_rule пользователь должен быть подключен к базе данных master.  
  
## <a name="example"></a>Пример  
 Следующий пример удаляет параметр брандмауэра уровня сервера с именем «Example setting 1». Выполните инструкцию в виртуальной базе данных master.  
  
```   
EXEC sp_delete_firewall_rule N'Example setting 1';   
```  
  
## <a name="see-also"></a>См. также:  
 [Брандмауэр базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Как настроить параметры брандмауэра (база данных SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sys. firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
  
  


