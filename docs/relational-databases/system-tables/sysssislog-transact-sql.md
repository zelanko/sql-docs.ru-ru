---
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
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe5d4d2b6475c8f46a7d47f3b8106772def6dfb7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689853"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой записи журнала, сформированной пакетами или их задачами и контейнерами во время выполнения. Эта таблица создается в базе данных msdb при установке служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если ведение журнала настроено таким образом, что записи вносятся в журнал другой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в указанной базе данных создается таблица sysssislog следующего формата.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] записи журнала в этой таблице **только** Если пакеты используют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистратор.  
  
  
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
 [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
