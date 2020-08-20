---
description: sysssislog (Transact-SQL)
title: sysssislog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9aef51cb3297cd83b68fa42c71dcd993fb418830
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473112"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит по одной строке для каждой записи журнала, сформированной пакетами или их задачами и контейнерами во время выполнения. Эта таблица создается в базе данных msdb при установке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Если ведение журнала настроено таким образом, что записи вносятся в журнал другой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в указанной базе данных создается таблица sysssislog следующего формата.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] записывает записи журнала в эту таблицу **только** в том случае, если пакеты используют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистратор.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**int**|Уникальный идентификатор для записи журнала.|  
|event|**sysname**|Имя события, которое сформировало запись журнала.|  
|computer|**nvarchar**|Компьютер, на котором был запущен пакет, когда была сформирована запись журнала.|  
|оператор|**nvarchar**|Имя пользователя сотрудника, запустившего пакет, который сформировал запись журнала.|  
|source|**nvarchar**|Имя исполняемого объекта в пакете, который сформировал запись журнала.|  
|sourceid|**uniqueidentifier**|Идентификатор GUID исполняемого объекта в пакете, который сформировал запись журнала.|  
|executionid|**uniqueidentifier**|Идентификатор GUID экземпляра выполнения исполняемого объекта, который сформировал запись журнала.|  
|starttime|**datetime**|Время начала выполнения пакета.|  
|endtime|**datetime**|Время завершения выполнения пакета.<br /><br /> Эта функция не реализована. Значение в столбце endtime всегда равно значению в столбце starttime.|  
|datacode|**int**|Необязательное целочисленное значение, которое обычно указывает на результат выполнения контейнера или задачи.|  
|databytes|**image**|Необязательный байтовый массив для хранения дополнительной информации.|  
|сообщение|**nvarchar**|Описание события и сведения, связанные с событием.|  
  
## <a name="see-also"></a>См. также:  
 [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
