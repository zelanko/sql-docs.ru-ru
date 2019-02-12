---
title: sp_delete_database_firewall_rule (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: eb8ee3482868f64765e7bf90e962c9756eadbdbc
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015105"
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Удаляет параметр брандмауэра уровня базы данных из вашего [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Правила брандмауэра базы данных можно настроить и удалить базу данных master и пользовательских баз данных на [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].   
  
 
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@name =**] **"**_имя_**"**  
 Имя параметра брандмауэра уровня базы данных, который будет удален. *имя* — **nvarchar(128)** без значения по умолчанию. Идентификатор Юникода `N` является необязательным для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
## <a name="permissions"></a>Разрешения  
 Только на уровне сервера имя входа субъекта созданное процесс подготовки или субъекта Azure Active Directory, назначены так, как администратор может удалить правила брандмауэра уровня базы данных.  
  
## <a name="example"></a>Пример  
 Следующий пример удаляет параметр брандмауэра уровня базы данных `Example DB Setting 1`.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>См. также  
 [Брандмауэр базы данных Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Как Настройка параметров брандмауэра (база данных Azure SQL)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


