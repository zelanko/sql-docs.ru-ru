---
title: sp_helpreplicationdboption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0376653d2466bf756ba76575f90841f78956ade7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718673"
---
# <a name="sp_helpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Отображает, доступны ли для репликации базы данных на издателе. Эта хранимая процедура выполняется на подписчике в любой базе данных. *Не поддерживается для издателей Oracle.*  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'`Имя базы данных. Аргумент *dbname* имеет тип **sysname**и значение по умолчанию **%** . Если **%** значение равно, результирующий набор будет содержать все базы данных на издателе; в противном случае возвращается информация только о указанной базе данных. Данные не возвращаются для тех баз данных, где у пользователя нет соответствующих описанных ниже разрешений.  
  
`[ @type = ] 'type'`Разрешает результирующий набор содержать только те базы данных, для которых было включено указанное значение *типа* параметра репликации. Аргумент *Type имеет тип* **sysname**и может принимать одно из следующих значений.  
  
|Применение|Описание:|  
|-----------|-----------------|  
|**отменить**|Разрешена репликация транзакций.|  
|**Публикация слиянием**|Разрешена репликация слиянием.|  
|**репликация разрешена** (по умолчанию)|Разрешена репликация транзакций или репликация слиянием.|  
  
`[ @reserved = ] reserved`Указывает, возвращаются ли сведения о существующих публикациях и подписках. *reserved* имеет **бит**и значение по умолчанию 0. Если значение равно **1**, результирующий набор содержит сведения о том, есть ли в указанной базе данных существующие публикации или подписки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных.|  
|**идентификатор**|**int**|Идентификатор базы данных.|  
|**transpublish**|**bit**|Значение, если для базы данных включена публикация моментальных снимков или публикации транзакций; значение **1** означает, что публикация моментального снимка или публикации транзакций включена.|  
|**mergepublish**|**bit**|Значение, если для базы данных включена публикация слиянием. значение **1** означает, что публикация слиянием включена.|  
|**dbowner**|**bit**|Если пользователь является членом предопределенной роли базы данных **db_owner** ; значение **1** указывает, что пользователь является членом этой роли.|  
|**dbreadonly**|**bit**|Имеет значение, если база данных помечена как доступная только для чтения; значение **1** означает, что база данных доступна только для чтения.|  
|**haspublications**|**bit**|Имеет значение, если база данных содержит какие-либо существующие публикации; значение **1** означает наличие существующих публикаций.|  
|**haspullsubscriptions**|**bit**|Имеет значение, если база данных содержит какие-либо существующие подписки по запросу; значение **1** означает, что существуют подписки по запросу.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpreplicationdboption** используется в репликации моментальных снимков, транзакций и репликация слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли сервера **sysadmin** могут выполнять **sp_helpreplicationdboption** для любой базы данных. Члены предопределенной роли базы данных **db_owner** могут выполнять **sp_helpreplicationdboption** для этой базы данных.  
  
## <a name="see-also"></a>См. также  
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
