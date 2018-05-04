---
title: представление sys.linked_logins (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8cb32cba07ae84c08dcf4ab51c28708960844401
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого сопоставления имени входа в связанный сервер, чтобы эту информацию можно было использовать в удаленных вызовах процедур и распределенных запросах от локального сервера к соответствующему связанному серверу.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера в **sys.servers**.|  
|**local_principal_id**|**int**|Участник сервера, к которому относится сопоставление.<br /><br /> 0 = шаблон или «public».|  
|**uses_self_credential**|**бит**|Если это значение равно 1, сопоставление показывает, что сеанс должен использовать собственные учетные данные; в противном случае значение 0 указывает, что в сеансе должны использоваться предоставленные имя и пароль.|  
|**remote_name**|**sysname**|Имя удаленного пользователя, используемое при подключении. Пароль также хранится, но доступ к нему через интерфейсы представления каталога не обеспечивается.|  
|**modify_date**|**datetime**|Дата последнего изменения связанного имени входа.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
