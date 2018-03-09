---
title: "sys.Routes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c06cefdc92f1d38fc0289e80549798d855509793
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данное представление каталога содержит одну строку для каждого маршрута. Компонент Service Broker использует маршруты для определения сетевого адреса службы.   
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя маршрута, уникальное в пределах базы данных. Не допускает значения NULL.|  
|**route_id**|**int**|Идентификатор маршрута. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор участника базы данных, которому принадлежит маршрут. Допускает значение NULL.|  
|**remote_service_name**|**nvarchar(256)**|Имя удаленной службы. Допускает значение NULL.|  
|**broker_instance**|**nvarchar(128)**|Идентификатор брокера, на котором расположена удаленная служба. Допускает значение NULL.|  
|**lifetime**|**datetime**|Дата и время истечения срока действия маршрута. Обратите внимание, что данное значение не использует местный часовой пояс. Вместо этого значение отображает время истечения срока действия в формате UTC. Допускает значение NULL.|  
|**address**|**nvarchar(256)**|Сетевой адрес, по которому компонент Service Broker отправляет сообщения удаленной службе. Допускает значение NULL.|  
|**mirror_address**|**nvarchar(256)**|Сетевой адрес участника зеркального отображения для сервера, указанного в адресе. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
