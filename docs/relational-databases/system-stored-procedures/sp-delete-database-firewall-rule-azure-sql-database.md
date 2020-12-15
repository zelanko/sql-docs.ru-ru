---
description: sp_delete_database_firewall_rule (база данных SQL Azure)
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
monikerRange: = azuresqldb-current
ms.openlocfilehash: ae71838bd9a384e616d0f1fe50d612535f840919
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472695"
---
# <a name="sp_delete_database_firewall_rule-azure-sql-database"></a>sp_delete_database_firewall_rule (база данных SQL Azure)
[!INCLUDE[Azure SQL Database](../../includes/applies-to-version/asdb.md)]

  Удаляет параметр брандмауэра уровня базы данных из [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Правила брандмауэра базы данных можно настроить и удалить для базы данных master, а также для пользовательских баз данных на [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] .   
  
 
## <a name="syntax"></a>Синтаксис  
  
```    
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 `[@name =] [N]'name'`  
 Имя параметра брандмауэра уровня базы данных, который будет удален. *имя* имеет тип **nvarchar (128)** без значения по умолчанию. Идентификатор Юникода `N` является необязательным для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] . 
  
## <a name="permissions"></a>Разрешения  
 Только имя входа субъекта уровня сервера, созданное процессом подготовки или участником Azure Active Directory, назначенным администратором, может удалять правила брандмауэра уровня базы данных.  
  
## <a name="example"></a>Пример  
 В следующем примере удаляется параметр брандмауэра уровня базы данных с именем `Example DB Setting 1` .
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Брандмауэр базы данных SQL Azure](/azure/azure-sql/database/firewall-configure)   
 [Как настроить параметры брандмауэра (база данных SQL Azure)](/azure/azure-sql/database/firewall-configure)   
 [sp_set_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;базе данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
