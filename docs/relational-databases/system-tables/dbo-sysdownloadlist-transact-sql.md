---
title: dbo. sysdownloadlist (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e888cc3d36b909035247d5f1c16dd1ab61e0d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061189"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит очередь инструкций по загрузке для всех целевых серверов.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Столбец идентификаторов, обеспечивающий естественную вставку последовательности строк.|  
|**source_server**|**имеет sysname**|Имя исходного сервера.|  
|**operation_code**|**tinyint**|Код операции для задания:<br /><br /> **1** = INS (вставка)<br /><br /> **2** = UPD (обновление)<br /><br /> **3** = Del (удаление)<br /><br /> **4** = запуск<br /><br /> **5** = завершение|  
|**object_type**|**tinyint**|Код типа объекта.|  
|**object_id** <sup>1</sup>|**UNIQUEIDENTIFIER**|Идентификационный номер объекта.|  
|**target_server**|**имеет sysname**|Имя целевого сервера.|  
|**error_message**|**nvarchar(1024)**|Сообщение об ошибке, если целевой сервер обнаруживает ошибку при обработке определенной строки.|  
|**date_posted**|**datetime**|Дата и время отправления задачи на целевой сервер.|  
|**date_downloaded**|**datetime**|Дата и время последней загрузки задания.|  
|**состояние**|**tinyint**|Состояние задания:<br /><br /> **0** = еще не скачан<br /><br /> **1** = успешно загружен|  
|**deleted_object_name**|**имеет sysname**|Имя удаленного объекта.|  
  
 <sup>1</sup> столбец **object_id** может иметь значение **-1**, которое соответствует значению ALL, если столбец **operation_code** является значением Delete.  
  
  
