---
description: Хранимая процедура sp_helpdistpublisher (Transact-SQL)
title: sp_helpdistpublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cb9bfd2bebe5220d992b92251c79df957f3d7077
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474092"
---
# <a name="sp_helpdistpublisher-transact-sql"></a>Хранимая процедура sp_helpdistpublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает свойства издателя, использующего распространитель. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` Издатель, для которого возвращаются свойства. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию **%** .  
  
`[ @check_user = ] check_user` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя издателя.|  
|**distribution_db**|**sysname**|База данных распространителя для указанного издателя.|  
|**security_mode**|**int**|Режим безопасности, используемый агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**пользователей**|**sysname**|Имя входа, используемое агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar (524)**|Возвращаемый пароль (в простой зашифрованной форме). Пароль имеет значение NULL для пользователей, отличных от **sysadmin**.|  
|**active**|**bit**|Использует ли удаленный издатель локальный сервер в качестве распространителя:<br /><br /> **0** = Нет<br /><br /> **1** = Да|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога.|  
|**trusted**|**bit**|Требуется ли пароль при подключении издателя к распространителю. Для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий этот параметр всегда должен возвращать значение **0**, означающее, что пароль является обязательным.|  
|**thirdparty_flag**|**bit**|Будет ли публикация включена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложением стороннего разработчика:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Oracle или издатель шлюза Oracle.<br /><br /> **1** = издатель интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложением стороннего производителя.|  
|**publisher_type**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **СУБД**<br /><br /> **ORACLE GATEWAY.**|  
|**publisher_data_source**|**nvarchar(4000)**|Имя источника данных OLE DB на издателе.|  
|**storage_connection_string**|**nvarchar(4000)**|Ключ доступа к хранилищу для рабочего каталога, когда распространитель или издатель в базе данных SQL Azure.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helpdistpublisher** используется во всех типах репликации.  
  
 **sp_helpdistpublisher** не будет отображать имя или пароль издателя в результирующем наборе для имен входа, не являющихся**администраторами** .  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли сервера **sysadmin** могут выполнять **Sp_helpdistpublisher** для любого издателя, использующего локальный сервер в качестве распространителя. Члены предопределенной роли базы данных **db_owner** или роли **replmonitor** в базе данных распространителя могут выполнять **sp_helpdistpublisher** для любого издателя, использующего эту базу данных распространителя. Пользователи из списка доступа к публикации для публикации на указанном *издателе* могут выполнять **sp_helpdistpublisher**. Если параметр *Publisher* не указан, возвращаются сведения для всех издателей, к которым у пользователя есть права доступа.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
