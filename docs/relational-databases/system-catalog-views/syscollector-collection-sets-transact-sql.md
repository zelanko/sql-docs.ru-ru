---
title: syscollector_collection_sets (Transact-SQL) | Документы Microsoft
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
- syscollector_collection_sets_TSQL
- syscollector_collection_sets
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collection_sets view
ms.assetid: db0def92-f25b-45da-9709-eab972b33800
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 72c2abe09766f62f2c261646bd0357116dacbffb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorcollectionsets-transact-sql"></a>syscollector_collection_sets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о наборе сбора, включая расписание, режим и состояние сбора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|collection_set_id|**int**|Локальный идентификатор набора элементов сбора. Не допускает значение NULL.|  
|collection_set_uid|**uniqueidentifier**|Глобальный уникальный идентификатор набора элементов сбора. Не допускает значение NULL.|  
|имя|**nvarchar(4000)**|Имя набора элементов сбора. Допускает значение NULL.|  
|target;|**nvarchar(max)**|Задает цель для набора элементов сбора. Допускает значение NULL.|  
|is_system|**бит**|Во включенном состоянии (1) означает, что набор сбора поставлялся вместе со сборщиком данных. Выключенное состояние (0) указывает на то, что набор сбора был добавлен пользователем dc_admin позже. Данный набор элементов сбора может быть пользовательским набором собственной или сторонней разработки. Не допускает значение NULL.|  
|is_running|**бит**|Указывает, работает ли набор элементов сбора. Не допускает значение NULL.|  
|collection_mode|**smallint**|Указывает режим сбора для указанного набора. Не допускает значение NULL.<br /><br /> Режим сбора может быть одним из следующих.<br /><br /> 0 — режим с кэшированием. Сбор и передача данных выполняются по отдельным расписаниям.<br /><br /> 1 — режим без кэширования. Сбор и передача данных выполняются по общему расписанию.|  
|proxy_id|**int**|Задает учетную запись-посредник, используемую для запуска шага задания набора сбора. Допускает значение NULL.|  
|schedule_uid|**uniqueidentifier**|Указатель на расписание набора элементов сбора. Допускает значение NULL.|  
|collection_job_id|**uniqueidentifier**|Идентифицирует задание сбора. Допускает значение NULL.|  
|upload_job_id|**uniqueidentifier**|Идентифицирует задание передачи сбора. Допускает значение NULL.|  
|logging_level|**smallint**|Задает уровень ведения журнала (0, 1 или 2). Не допускает значение NULL.|  
|days_until_expiration|**smallint**|Число дней, в течение которых собранные данные хранятся в хранилище данных управления. Не допускает значение NULL.|  
|description|**nvarchar(4000)**|Содержит описание набора элементов сбора. Допускает значение NULL.|  
|dump_on_any_error|**бит**|Включен (1) или off (0), чтобы указать, следует ли создавать [!INCLUDE[ssIS](../../includes/ssis-md.md)] файл дампа при любых ошибках. Не допускает значение NULL.|  
|dump_on_codes|**nvarchar(max)**|Содержит список кодов ошибок служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], которые используются для включения файла дампа. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для роли dc_operator, dc_proxy.  
  
## <a name="remarks"></a>Замечания  
 API-интерфейс сборщика данных позволяет изменять и удалять только собственные наборы элементов сбора. Наборы сбора, поставляемые вместе с системой, нельзя изменять или удалять. Однако можно включать или отключать системный набор элементов сбора и менять его конфигурацию.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
