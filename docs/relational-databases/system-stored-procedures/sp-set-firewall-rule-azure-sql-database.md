---
description: sp_set_firewall_rule (база данных SQL Azure)
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
monikerRange: = azuresqldb-current || = azure-sqldw-latest
ms.openlocfilehash: 795aeb9a03f839cae400e92060ac21056f314d2f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468285"
---
# <a name="sp_set_firewall_rule-azure-sql-database"></a>sp_set_firewall_rule (база данных SQL Azure)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  Создает или обновляет параметры брандмауэра для сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Эта хранимая процедура доступна только в базе данных master для имени входа субъекта уровня сервера или назначенного Azure Active Directory участника.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 В следующей таблице показаны поддерживаемые аргументы и параметры в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] .  
  
|Имя|Datatype|Описание|  
|----------|--------------|-----------------|  
|[ @name =] "имя"|**NVARCHAR (128)**|Имя, используемое для описания и определения параметров брандмауэра на уровне сервера.|  
|[ @start_ip_address =] "start_ip_address"|**VARCHAR (50)**|Наименьший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые больше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наименьший возможный IP-адрес: `0.0.0.0`.|  
|[ @end_ip_address =] "end_ip_address"|**VARCHAR (50)**|Наибольший IP-адрес в диапазоне параметра брандмауэра на уровне сервера. IP-адреса, которые меньше этого адреса или равны ему, могут попытаться подключиться к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Наибольший возможный IP-адрес: `255.255.255.255`.<br /><br /> Примечание. попытки подключения Azure разрешены, если это поле и поле *start_ip_address* равны `0.0.0.0` .|  
  
## <a name="remarks"></a>Комментарии  
 Имена настроек брандмауэра на уровне сервера должны быть уникальными. Если имя параметра, указанного для хранимой процедуры, уже существует в таблице параметров брандмауэра, начальный и конечный IP-адреса будут обновлены. В противном случае будет создан новый параметр брандмауэра на уровне сервера.  
  
 Добавление параметра брандмауэра уровня сервера, для которого начальный и конечный IP-адреса равны `0.0.0.0`, позволяет разрешить доступ к серверу [!INCLUDE[ssSDS](../../includes/sssds-md.md)] из Azure. Укажите значение параметра *Name* , которое поможет вам запомнить параметры брандмауэра на уровне сервера.  
  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Только имя входа субъекта уровня сервера, созданное процессом подготовки или участником Azure Active Directory, назначенным администратором, может создавать или изменять правила брандмауэра на уровне сервера. Для выполнения sp_set_firewall_rule пользователь должен быть подключен к базе данных master.  
  
## <a name="examples"></a>Примеры  
 Приведенный ниже код создает параметр брандмауэра уровня сервера с именем `Allow Azure`, разрешающий доступ из Azure. Выполните следующую инструкцию в виртуальной базе данных master.  
  
```  
-- Enable Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Следующий код создает параметр брандмауэра уровня сервера `Example setting 1` только для IP-адреса `0.0.0.2`. Затем `sp_set_firewall_rule` хранимая процедура вызывается снова для обновления конечного IP-адреса на `0.0.0.4` , в этом параметре брандмауэра. При этом создается диапазон, который разрешает IP-адресам `0.0.0.2` , `0.0.0.3` и `0.0.0.4` доступ к серверу.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Брандмауэр базы данных SQL Azure](/azure/azure-sql/database/firewall-configure)   
 [Как настроить параметры брандмауэра (база данных SQL Azure)](/azure/azure-sql/database/firewall-configure)   
 [sys.firewall_rules &#40;базе данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)