---
title: sys.database_firewall_rules (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e224bec27ba3151fb531f5ad0ce9676a4e3a8d2e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789512"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о параметрах брандмауэра уровня базы данных, связанных с вашей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Параметры брандмауэра уровня базы данных особенно полезны при использовании пользователей автономной базы данных. Дополнительные сведения см. в разделе [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 Представление `sys.database_firewall_rules` содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**INTEGER**|Идентификатор параметра брандмауэра на уровне базы данных.|  
|name|**NVARCHAR(128)**|Имя, выбранное для описания и определения параметров брандмауэра на уровне базы данных.|  
|start_ip_address|**VARCHAR(50)**|Самый маленький IP-адрес в диапазоне параметра брандмауэра на уровне базы данных. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`.|  
|end_ip_address|**VARCHAR(50)**|Самый большой IP-адрес в диапазоне параметра брандмауэра. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`.<br /><br /> Примечание: Windows попытки подключения к Azure разрешены, если это поле и **start_ip_address** поле equals `0.0.0.0`.|  
|create_date|**ДАТЫ И ВРЕМЕНИ**|Дата и время создания параметра брандмауэра на уровне базы данных в формате UTC.|  
|modify_date|**ДАТЫ И ВРЕМЕНИ**|Дата и время последнего изменения параметра брандмауэра на уровне базы данных в формате UTC.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы удалить правило брандмауэра базы данных, используйте [sp_delete_database_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md). Чтобы задать правило брандмауэра для всех [!INCLUDE[ssSDS](../../includes/sssds-md.md)], см. в разделе [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md). Чтобы получить сведения о существующей базы данных правила брандмауэра, запросите [sys.database_firewall_rules (база данных SQL Azure)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно в **master** базы данных и в каждой пользовательской базы данных. Доступ только для чтения к этому представлению имеют все пользователи с разрешением на подключение к базе данных.  
  
## <a name="see-also"></a>См. также  
 [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules (база данных SQL Azure)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [Настройка брандмауэра Windows для доступа к ядру СУБД](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Настройка брандмауэра для доступа к данным FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [настроить брандмауэр для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
