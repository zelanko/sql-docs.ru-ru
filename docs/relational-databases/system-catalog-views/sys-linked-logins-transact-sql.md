---
title: sys.linked_logins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 712d5286036aa8fbf375d16abfbe3a3c2257ab91
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63004273"
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого сопоставления имени входа в связанный сервер, чтобы эту информацию можно было использовать в удаленных вызовах процедур и распределенных запросах от локального сервера к соответствующему связанному серверу.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера в **sys.servers**.|  
|**local_principal_id**|**int**|Участник сервера, к которому относится сопоставление.<br /><br /> 0 = шаблон или «public».|  
|**uses_self_credential**|**bit**|Если это значение равно 1, сопоставление показывает, что сеанс должен использовать собственные учетные данные; в противном случае значение 0 указывает, что в сеансе должны использоваться предоставленные имя и пароль.|  
|**remote_name**|**sysname**|Имя удаленного пользователя, используемое при подключении. Пароль также хранится, но доступ к нему через интерфейсы представления каталога не обеспечивается.|  
|**modify_date**|**datetime**|Дата последнего изменения связанного имени входа.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
