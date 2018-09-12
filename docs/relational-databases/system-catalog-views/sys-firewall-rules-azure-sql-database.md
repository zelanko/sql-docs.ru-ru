---
title: sys.firewall_rules (база данных SQL Azure) | Документация Майкрософт
ms.date: 03/14/2017
ms.prod: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.firewall_rules
- firewall_rules
- sys.firewall_rules_TSQL
- firewall_rules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- firewall_rules
- sys.firewall_rules
ms.assetid: 140d2cd8-9aa1-4cc5-870d-e1dbc873b3fe
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 37313fc7aa6bfe29622bb6ec6900120a89e68dff
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820530"
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о параметрах брандмауэра уровня сервера, связанных с вашей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Представление `sys.firewall_rules` содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**INT**|Идентификатор параметра брандмауэра на уровне сервера.|  
|name|**NVARCHAR(128)**|Имя, выбранное для описания и определения параметров брандмауэра на уровне сервера.|  
|start_ip_address|**VARCHAR(50)**|Наименьший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`.|  
|end_ip_address|**VARCHAR(50)**|Наибольший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`.<br /><br /> Примечание: Windows попытки подключения к Azure разрешены, если это поле и **start_ip_address** поле equals `0.0.0.0`.|  
|create_date|**ДАТЫ И ВРЕМЕНИ**|Дата и время создания параметра брандмауэра на уровне сервера в формате UTC.<br /><br /> Примечание: В формате UTC — это сокращение от формате UTC.|  
|modify_date|**ДАТЫ И ВРЕМЕНИ**|Дата и время последнего изменения параметра брандмауэра на уровне сервера в формате UTC.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы удалить правило брандмауэра базы данных, используйте [sp_delete_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md). Чтобы задать правило брандмауэра для отдельной базы данных, см. в разделе [sys.database_firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md). Чтобы получить сведения о существующих правилах брандмауэра, запросите sys.firewall_rules (база данных SQL Azure).  
  
## <a name="permissions"></a>Разрешения  
 Доступ только для чтения к этому представлению доступна для всех пользователей с разрешением на подключение к **master** базы данных.  
  
## <a name="see-also"></a>См. также  
 [sys.database_firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Настройка брандмауэра Windows для доступа к ядру СУБД](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Настройка брандмауэра для доступа к данным FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [Настройка брандмауэра для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [Практическое руководство. Настройка параметров брандмауэра для базы данных SQL с помощью портала Azure](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)  
  
  
