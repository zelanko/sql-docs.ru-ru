---
title: sys.event_notifications (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- event_notifications_TSQL
- event_notifications
- sys.event_notifications_TSQL
- sys.event_notifications
dev_langs:
- TSQL
helpviewer_keywords:
- sys.event_notifications catalog view
ms.assetid: 136a76ee-2b35-4418-ab46-fda2d51f7d99
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 60fb1fd10b448e7dc71d06aecaa36385f882f62f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755182"
---
# <a name="syseventnotifications-transact-sql"></a>sys.event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого объекта, являющегося уведомление о событии, с помощью **sys.objects.type** = EN.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя уведомления о событии.|  
|**object_id**|**int**|Идентификационный номер объекта. Уникален в базе данных.|  
|**parent_class**|**tinyint**|Класс родителя.<br /><br /> 0 = база данных;<br /><br /> 1 = объект или столбец|  
|**parent_class_desc**|**nvarchar(60)**|DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_ID**|**int**|Ненулевой идентификатор родительского объекта.<br /><br /> 0 = родительский класс — база данных|  
|**create_date**|**datetime**|Дата создания.|  
|**modify_date**|**datetime**|Всегда равна **create_date**.|  
|**service_name**|**nvarchar(256)**|Имя целевой службы, куда посылается уведомление.|  
|**broker_instance**|**nvarchar(128)**|Экземпляр посредника, которому отправляют уведомление.|  
|**principal_id**|**int**|Идентификатор участника базы данных, являющегося хозяином этого уведомления о событии.|  
|**creator_sid**|**varbinary(85)**|Идентификатор безопасности имени входа, под которым создано уведомление о событии.<br /><br /> Если параметр FAN_IN не указан, имеет значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
