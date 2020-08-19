---
description: sys.database_firewall_rules (база данных SQL Azure)
title: sys. database_firewall_rules (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 49a48533c800093090465819610052009633839f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475476"
---
# <a name="sysdatabase_firewall_rules-azure-sql-database"></a>sys.database_firewall_rules (база данных SQL Azure)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Возвращает сведения о параметрах брандмауэра уровня базы данных, связанных с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Параметры брандмауэра уровня базы данных особенно полезны при использовании пользователей автономной базы данных. Дополнительные сведения см. в разделе [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 Представление `sys.database_firewall_rules` содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**ЦЕЛО**|Идентификатор параметра брандмауэра на уровне базы данных.|  
|name|**NVARCHAR (128)**|Имя, выбранное для описания и определения параметров брандмауэра на уровне базы данных.|  
|start_ip_address|**VARCHAR (45)**|Самый маленький IP-адрес в диапазоне параметра брандмауэра на уровне базы данных. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`.|  
|end_ip_address|**VARCHAR (45)**|Самый большой IP-адрес в диапазоне параметра брандмауэра. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`.<br /><br /> Примечание. попытки подключения Azure разрешены, если это поле и поле **start_ip_address** равны `0.0.0.0` .|  
|create_date|**DATETIME**|Дата и время создания параметра брандмауэра на уровне базы данных в формате UTC.|  
|modify_date|**DATETIME**|Дата и время последнего изменения параметра брандмауэра на уровне базы данных в формате UTC.|  
  
## <a name="remarks"></a>Комментарии  
 Чтобы получить сведения о параметрах брандмауэра на уровне сервера, связанных с База данных SQL Microsoft Azure, используйте представление [sys. firewall_rules (база данных SQL Azure)](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно в базе данных **master** и в каждой пользовательской базе данных. Доступ только для чтения к этому представлению имеют все пользователи с разрешением на подключение к базе данных.  
  
## <a name="see-also"></a>См. также
[sp_set_database_firewall_rule (база данных Azure SQL)](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sp_set_firewall_rule (база данных Azure SQL)](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sys. firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
[Настройка брандмауэра Windows для доступа к ядро СУБД](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Настройка брандмауэра для доступа к FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[настроить брандмауэр для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
