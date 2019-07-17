---
title: sp_set_firewall_rule (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 436396ed0982b12fffd5b894cb4c2a4006484ab0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104434"
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Создает или обновляет параметры брандмауэра для сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Эта хранимая процедура доступна только в базе данных master имя входа субъекта уровня сервера или назначенных субъекту-Azure Active Directory.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 В следующей таблице показаны поддерживаемые аргументы и параметры в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Name|Datatype|Описание|  
|----------|--------------|-----------------|  
|[@name =] «name»|**NVARCHAR(128)**|Имя, используемое для описания и определения параметров брандмауэра на уровне сервера.|  
|[@start_ip_address =] 'start_ip_address»|**VARCHAR(50)**|Наименьший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`.|  
|[@end_ip_address =] 'end_ip_address»|**VARCHAR(50)**|Наибольший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`.<br /><br /> Примечание. Попытки подключения к Azure разрешены, если это поле и *start_ip_address* поле equals `0.0.0.0`.|  
  
## <a name="remarks"></a>Примечания  
 Имена настроек брандмауэра на уровне сервера должны быть уникальными. Если имя параметра, указанного для хранимой процедуры, уже существует в таблице параметров брандмауэра, начальный и конечный IP-адреса будут обновлены. В противном случае будет создан новый параметр брандмауэра на уровне сервера.  
  
 При добавлении параметра брандмауэра уровня сервера, в котором начальный и конечный IP-адреса равны `0.0.0.0`, позволяет разрешить доступ к вашей [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server из Azure. Укажите значение для *имя* параметр, который поможет запомнить предназначение параметра брандмауэра уровня сервера.  
  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Только на уровне сервера имя входа субъекта созданное процессом подготовки или субъекта Azure Active Directory, назначены так, как администратора можно создать или изменить правила брандмауэра уровня сервера. Пользователь должен быть подключен к базе данных master, чтобы выполнить хранимую процедуру sp_set_firewall_rule.  
  
## <a name="examples"></a>Примеры  
 Следующий код создает параметр брандмауэра уровня сервера `Allow Azure` , разрешающий доступ из Azure. Выполните следующую команду в виртуальной базе данных master.  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Следующий код создает параметр брандмауэра уровня сервера `Example setting 1` только для IP-адреса `0.0.0.2`. Затем `sp_set_firewall_rule` снова вызывается хранимая процедура для обновления конечный IP-адрес для `0.0.0.4`, в том, что параметр брандмауэра. При этом создается диапазон, что позволяет IP-адреса `0.0.0.2`, `0.0.0.3`, и `0.0.0.4` доступ к серверу.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>См. также  
 [Брандмауэр базы данных Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Практическое руководство. Настройка параметров брандмауэра (база данных Azure SQL)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys.firewall_rules &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
