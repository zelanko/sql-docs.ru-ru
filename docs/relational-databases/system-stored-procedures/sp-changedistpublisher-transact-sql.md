---
title: sp_changedistpublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ce38cf053b16ae43ab9a9c5cd617bace6d78e4db
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085956"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства распространяющего издателя. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=** ] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@property=** ] **"***свойство***"**  
 Свойство, изменяемое для данного издателя. *Свойство* — **sysname** и может принимать одно из следующих значений.  
  
 [ **@value=** ] **'***value***'**  
 Значение для заданного свойства. *значение* — **nvarchar(255)**, значение по умолчанию NULL.  
  
 [  **@storage_connection_string =**] **"***storage_connection_string***"**  
 Является обязательным для базы данных SQL управляемого экземпляра, должно соответствовать ключу доступа для объема хранилища базы данных SQL Azure. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 В следующей таблице описаны свойства издателей и значения этих свойств.  
  
|Свойство|Значения|Описание|  
|--------------|------------|-----------------|  
|**Active**|**true**|Активирует издатель.|  
||**false**|Отключает издатель.|  
|**distribution_db**||Имя базы данных распространителя.|  
|**Имя входа**||Имя входа.|  
|**password**||Надежный пароль для указанного имени входа.|  
|**security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows. *Это единственно возможный отличается от* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *издателя.*|  
||**0**|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Это единственно возможный отличается от* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *издателя.*|  
|**working_directory**||Рабочий каталог, в котором хранятся данные и файлы схемы для публикации.|  
|NULL (по умолчанию)||Все доступные *свойство* параметры печати.| 
|**storage_connection_string**| Ключ доступа | Ключ доступа для рабочего каталога при работе Azure базы данных SQL управляемого экземпляра базы данных. 
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changedistpublisher** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_changedistpublisher**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
