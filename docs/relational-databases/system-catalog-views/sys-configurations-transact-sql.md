---
title: sys.Configurations (Transact-SQL) | Документы Microsoft
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
- sys.configurations_TSQL
- configurations
- sys.configurations
- configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.configurations catalog view
ms.assetid: c4709ed1-bf88-4458-9e98-8e9b78150441
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b7031d6f0999a29c8baf10ba36565fba6b117a55
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого значения параметра конфигурации сервера в системе.  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Уникальный идентификатор значения конфигурации.|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**value**|**sql_variant**|Установленное значение параметра.|  
|**minimum**|**sql_variant**|Минимальное значение параметра конфигурации.|  
|**maximum**|**sql_variant**|Максимальное значение параметра конфигурации.|  
|**value_in_use**|**sql_variant**|Текущее значение параметра.|  
|**Описание**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**is_dynamic**|**бит**|1 = переменная, вступающая в силу после выполнения инструкции RECONFIGURE.|  
|**is_advanced**|**бит**|1 = переменная отображается только тогда, когда **Показать advancedoption** имеет значение.|  
  
 Список всех параметров конфигурации сервера см. в разделе [параметры конфигурации сервера &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
> [!NOTE]  
>  Параметры конфигурации уровня базы данных см. в разделе [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Для настройки программной архитектуры NUMA см [программной архитектуры NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога конфигурации уровня сервера &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
