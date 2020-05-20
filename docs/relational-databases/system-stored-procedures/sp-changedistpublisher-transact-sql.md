---
title: sp_changedistpublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb90ec6a3d5413d22f4721491d3b151a7e28ac05
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833440"
---
# <a name="sp_changedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @property = ] 'property'`Свойство, которое необходимо изменить для данного издателя. *свойство* имеет тип **sysname** и может принимать одно из следующих значений.  
  
`[ @value = ] 'value'`Значение для данного свойства. *value* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @storage_connection_string = ] 'storage_connection_string'`Требуется для управляемого экземпляра базы данных SQL. он должен соответствовать ключу доступа для тома хранилища базы данных SQL Azure. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 В следующей таблице описаны свойства издателей и значения этих свойств.  
  
|Свойство|Значения|Описание|  
|--------------|------------|-----------------|  
|**active**|**true**|Активирует издатель.|  
||**false**|Отключает издатель.|  
|**distribution_db**||Имя базы данных распространителя.|  
|**пользователей**||Имя входа.|  
|**password**||Надежный пароль для указанного имени входа.|  
|**security_mode**|**1**|При подключении к подписчику используется проверка подлинности Windows. *Его нельзя изменить для не относящегося к* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *издатель.*|  
||**0**;|При подключении к издателю используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Его нельзя изменить для не относящегося к* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *издатель.*|  
|**working_directory**||Рабочий каталог, в котором хранятся данные и файлы схемы для публикации.|  
|NULL (по умолчанию)||Выводятся все доступные параметры *свойств* .| 
|**storage_connection_string**| Ключ доступа | Ключ доступа для рабочего каталога при Управляемый экземпляр Базы данных SQL Azure базы данных. 
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changedistpublisher** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changedistpublisher**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств распространителя и издателя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
