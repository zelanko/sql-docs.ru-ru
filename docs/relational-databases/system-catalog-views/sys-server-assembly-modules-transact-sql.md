---
title: sys.server_assembly_modules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
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
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53e1bb84d002322cd4bb9b1443502be0eae47e24
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке о каждом модуле сборки триггеров серверного уровня типа TA. Это представление сопоставляет триггеры сборок с базовой реализацией среды CLR. Можно соединить это отношение к **sys.server_triggers**. Сборка должна быть загружена в **master** базы данных. Ключом отношения является кортеж (object_id).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Обратная ссылка внешнего ключа (FOREIGN KEY) на объект, для которого определен данный модуль сборки.|  
|**assembly_id**|**int**|Идентификатор той сборки, откуда был создан этот модуль. Сборка должна быть загружена в базу данных master.|  
|**assembly_class**|**sysname**|Имя класса, входящего в сборку и определяющего данный модуль.|  
|**assembly_method**|**sysname**|Имя метода в классе, определяющем данный модуль. В случае агрегатных функций имеет значение NULL.|  
|**execute_as_principal_id**|**int**|Идентификатор сервера-участника, входящего в предложение EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> Идентификатор заданного участника, если выполнение AS SELF EXECUTE AS \<основной >.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Объект представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
