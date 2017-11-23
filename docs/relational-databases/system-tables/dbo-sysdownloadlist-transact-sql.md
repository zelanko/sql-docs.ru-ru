---
title: "dbo.sysdownloadlist (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs: TSQL
helpviewer_keywords: sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64ab3c661ff3cb5aa92d11e8193680629af9851b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит очередь инструкций по загрузке для всех целевых серверов.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Столбец идентификаторов, обеспечивающий естественную вставку последовательности строк.|  
|**source_server**|**sysname**|Имя исходного сервера.|  
|**operation_code**|**tinyint**|Код операции для задания:<br /><br /> **1** = МОДУЛИ (INSERT)<br /><br /> **2** = UPD (ОБНОВЛЕНИЕ)<br /><br /> **3** = DEL (DELETE)<br /><br /> **4** = НАЧАЛО<br /><br /> **5** = ОСТАНОВИТЬ|  
|**object_type**|**tinyint**|Код типа объекта.|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Идентификационный номер объекта.|  
|**целевой_сервер**|**sysname**|Имя целевого сервера.|  
|**функция ERROR_MESSAGE**|**nvarchar(1024)**|Сообщение об ошибке, если целевой сервер обнаруживает ошибку при обработке определенной строки.|  
|**date_posted**|**datetime**|Дата и время отправления задачи на целевой сервер.|  
|**date_downloaded**|**datetime**|Дата и время последней загрузки задания.|  
|**status**|**tinyint**|Состояние задания:<br /><br /> **0** = еще не загружено<br /><br /> **1** = успешно загружено|  
|**deleted_object_name**|**sysname**|Имя удаленного объекта.|  
  
 <sup>1</sup> **object_id** столбец может быть значение **-1**, который соответствует значение ALL, если **operation_code** столбец имеет значение DELETE.  
  
  
