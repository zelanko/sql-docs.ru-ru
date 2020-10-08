---
description: sp_set_database_firewall_rule (база данных SQL Azure)
title: sp_set_database_firewall_rule
titleSuffix: Azure SQL Database
ms.date: 08/04/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_database_firewall_rule
- sp_set_database_firewall_rule_TSQL
- sys.sp_set_database_firewall_rule
- sys.sp_set_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_database_firewall_rule
- firewall_rules, setting database rules
ms.assetid: 8f0506b6-a4ac-4e4d-91db-8077c40cb17a
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: 0b6f9130a4250bdb6f9c250bacbcaaa3943eeef3
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810507"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (база данных SQL Azure)
[!INCLUDE[Azure SQL Database](../../includes/applies-to-version/asdb.md)]

  Создает или обновляет правила брандмауэра уровня базы данных для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Правила брандмауэра базы данных можно настроить для базы данных **master** и для пользовательских баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] . Правила брандмауэра базы данных особенно полезны при использовании пользователей автономной базы данных. Дополнительные сведения см. в разделе [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] [N]'name'` Имя, используемое для описания и различения параметра брандмауэра уровня базы данных. *имя* имеет тип **nvarchar (128)** без значения по умолчанию. Идентификатор Юникода `N` является необязательным для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] . 
  
`[ @start_ip_address = ] 'start_ip_address'` Самый низкий IP-адрес в диапазоне параметра брандмауэра уровня базы данных. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`. *start_ip_address* имеет тип **varchar (50)** и не имеет значения по умолчанию.  
  
`[ @end_ip_address = ] 'end_ip_address'` Самый высокий IP-адрес в диапазоне параметра брандмауэра уровня базы данных. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`. *end_ip_address* имеет тип **varchar (50)** и не имеет значения по умолчанию.  
  
 В следующей таблице показаны поддерживаемые аргументы и параметры в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
  
> [!NOTE]  
>  Попытки подключения к Azure разрешены, если это поле и поле *start_ip_address* равны `0.0.0.0` .  
  
## <a name="remarks"></a>Комментарии  
 Имена настроек брандмауэра на уровне базы данных должны быть уникальными. Если имя параметра брандмауэра на уровне базы данных, указанного для хранимой процедуры, уже существует в таблице параметров брандмауэра уровня базы данных, начальный и конечный IP-адреса будут обновлены. В противном случае будет создан новый параметр брандмауэра на уровне базы данных.  
  
 При добавлении параметра брандмауэра уровня базы данных, в котором начальный и конечный IP-адреса равны `0.0.0.0` , вы включаете доступ к базе данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервере из любого ресурса Azure. Укажите значение параметра *Name* , которое поможет вспомнить, для чего предназначен параметр брандмауэра.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **CONTROL** для базы данных.  
  
## <a name="examples"></a>Примеры  
 Приведенный ниже код создает параметр брандмауэра уровня базы данных с именем `Allow Azure`, разрешающий доступ из Azure к этой базе данных.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Следующий код создает параметр брандмауэра уровня базы данных `Example DB Setting 1` только для IP-адреса `0.0.0.4`. Затем `sp_set_database firewall_rule` хранимая процедура вызывается снова для обновления конечного IP-адреса на `0.0.0.6` , в этом параметре брандмауэра. При этом создается диапазон, который разрешает IP-адресам `0.0.0.4` , `0.0.0.5` и `0.0.0.6` доступ к базе данных.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Брандмауэр базы данных SQL Azure](/azure/azure-sql/database/firewall-configure)   
 [Как настроить параметры брандмауэра (база данных SQL Azure)](/azure/azure-sql/database/firewall-configure)   
 [sp_set_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;базе данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
