---
title: sp_set_database_firewall_rule (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
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
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 93acd6ad9e904e1e3db5dfe7e244b459e7853d70
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025465"
---
# <a name="spsetdatabasefirewallrule-azure-sql-database"></a>sp_set_database_firewall_rule (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Создает или обновляет правила брандмауэра уровня базы данных для вашей [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Правила брандмауэра базы данных можно настроить для **master** базы данных и для пользовательских баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Правила брандмауэра базы данных особенно полезны при использовании автономных пользователей базы данных. Дополнительные сведения см. в разделе [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **[@name**  =] [N] "*имя*"  
 Имя, используемое для описания и определения параметров брандмауэра на уровне базы данных. *имя* — **nvarchar(128)** без значения по умолчанию. Идентификатор Юникода `N` является необязательным для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
 **[@start_ip_address** =] '*start_ip_address*'  
 Самый маленький IP-адрес в диапазоне параметра брандмауэра на уровне базы данных. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`. *start_ip_address* — **varchar(50)** без значения по умолчанию.  
  
 [**@end_ip_address** =] '*end_ip_address*'  
 Самый большой IP-адрес в диапазоне параметра брандмауэра на уровне базы данных. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к экземпляру служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`. *end_ip_address* — **varchar(50)** без значения по умолчанию.  
  
 В следующей таблице показаны поддерживаемые аргументы и параметры в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!NOTE]  
>  Попытки подключения к Azure разрешены, если это поле и *start_ip_address* поле equals `0.0.0.0`.  
  
## <a name="remarks"></a>Примечания  
 Имена настроек брандмауэра на уровне базы данных должны быть уникальными. Если имя параметра брандмауэра на уровне базы данных, указанного для хранимой процедуры, уже существует в таблице параметров брандмауэра уровня базы данных, начальный и конечный IP-адреса будут обновлены. В противном случае будет создан новый параметр брандмауэра на уровне базы данных.  
  
 При добавлении параметра брандмауэра уровня базы данных, в котором начальный и конечный IP-адреса равны `0.0.0.0`, предоставляется доступ к базе данных в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера из любой ресурс Azure. Укажите значение для *имя* параметр, который поможет запомнить предназначение параметра брандмауэра.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **CONTROL** для базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующий код создает параметр брандмауэра уровня базы данных `Allow Azure` , разрешающий доступ к базе данных из Azure.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Следующий код создает параметр брандмауэра уровня базы данных `Example DB Setting 1` только для IP-адреса `0.0.0.4`. Затем `sp_set_database firewall_rule` снова вызывается хранимая процедура для обновления конечный IP-адрес для `0.0.0.6`, в том, что параметр брандмауэра. При этом создается диапазон, что позволяет IP-адреса `0.0.0.4`, `0.0.0.5`, и `0.0.0.6` для доступа к базе данных.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>См. также  
 [Брандмауэр базы данных Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Как Настройка параметров брандмауэра (база данных Azure SQL)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;базы данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
