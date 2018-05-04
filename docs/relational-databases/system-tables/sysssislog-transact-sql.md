---
title: sysssislog (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
caps.latest.revision: 40
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0c3c61615204ee0ad52507fd3b1e0193e9d10343
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой записи журнала, сформированной пакетами или их задачами и контейнерами во время выполнения. Эта таблица создается в базе данных msdb при установке служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если ведение журнала настроено таким образом, что записи вносятся в журнал другой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в указанной базе данных создается таблица sysssislog следующего формата.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] записи журнала в этой таблице **только** при использовании пакетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистратор.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**int**|Уникальный идентификатор для записи журнала.|  
|event|**sysname**|Имя события, которое сформировало запись журнала.|  
|computer|**nvarchar**|Компьютер, на котором был запущен пакет, когда была сформирована запись журнала.|  
|оператор|**nvarchar**|Имя пользователя сотрудника, запустившего пакет, который сформировал запись журнала.|  
|источник|**nvarchar**|Имя исполняемого объекта в пакете, который сформировал запись журнала.|  
|sourceid|**uniqueidentifier**|Идентификатор GUID исполняемого объекта в пакете, который сформировал запись журнала.|  
|executionid|**uniqueidentifier**|Идентификатор GUID экземпляра выполнения исполняемого объекта, который сформировал запись журнала.|  
|starttime|**datetime**|Время начала выполнения пакета.|  
|endtime|**datetime**|Время завершения выполнения пакета.<br /><br /> Эта функция не реализована. Значение в столбце endtime всегда равно значению в столбце starttime.|  
|datacode|**int**|Необязательное целочисленное значение, которое обычно указывает на результат выполнения контейнера или задачи.|  
|databytes|**image**|Необязательный байтовый массив для хранения дополнительной информации.|  
|message|**nvarchar**|Описание события и сведения, связанные с событием.|  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services & #40; Службы SSIS & #41; Ведение журнала](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
