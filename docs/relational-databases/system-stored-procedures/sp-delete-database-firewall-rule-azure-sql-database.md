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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 660405e7e7592557422e43655c35ec27c194aad3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130684"
---
# <a name="sp_delete_database_firewall_rule-azure-sql-database"></a>sp_delete_database_firewall_rule (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Удаляет параметр брандмауэра уровня базы данных из [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Правила брандмауэра базы данных можно настроить и удалить для базы данных master, а также для пользовательских баз [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]данных на.   
  
 
## <a name="syntax"></a>Синтаксис  
  
```    
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 `[@name =] [N]'name'`  
 Имя параметра брандмауэра уровня базы данных, который будет удален. *имя* имеет тип **nvarchar (128)** без значения по умолчанию. Идентификатор `N` Юникода является необязательным для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
## <a name="permissions"></a>Разрешения  
 Только имя входа субъекта уровня сервера, созданное процессом подготовки или участником Azure Active Directory, назначенным администратором, может удалять правила брандмауэра уровня базы данных.  
  
## <a name="example"></a>Пример  
 В следующем примере удаляется параметр брандмауэра уровня базы данных с `Example DB Setting 1`именем.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Брандмауэр базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Как настроить параметры брандмауэра (база данных SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


