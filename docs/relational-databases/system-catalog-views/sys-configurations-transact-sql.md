---
title: sys. configurations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9eb9ced4e010001f42e106ce8b1903e029f2f1c4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109561"
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого значения параметра конфигурации сервера в системе.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Уникальный идентификатор значения конфигурации.|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**value**|**sql_variant**|Установленное значение параметра.|  
|**минимальное**|**sql_variant**|Минимальное значение параметра конфигурации.|  
|**maximum**|**sql_variant**|Максимальное значение параметра конфигурации.|  
|**value_in_use**|**sql_variant**|Текущее значение параметра.|  
|**nописание**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**is_dynamic**|**bit**|1 = переменная, вступающая в силу после выполнения инструкции RECONFIGURE.|  
|**is_advanced**|**bit**|1 = переменная отображается, только если задан параметр **Показать адванцедоптион** .|  
  
 Список всех параметров конфигурации сервера см. в разделе [Параметры конфигурации сервера &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
> [!NOTE]  
>  Сведения о параметрах конфигурации уровня базы данных см. в разделе [ALTER DATABASE scoped configuration &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Сведения о настройке программной архитектуры NUMA см. в разделе [Soft-numa &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога конфигурации на уровне сервера &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
