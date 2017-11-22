---
title: "SQL Server, объект Columnstore | Документация Майкрософт"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb0f5a1872802fc5f623650902ab7a92fe72c6e0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-columnstore-object"></a>SQL Server, объект Columnstore
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Объект **SQLServer:Columnstore** предоставляет счетчики для наблюдения за выполнением индекса columnstore в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В приведенной ниже таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Columnstore** .  
  
|Счетчики Columnstore|Описание|  
|--------------------------|-----------------|  
|**Закрыто разностных групп строк**|Количество закрытых разностных групп строк.|  
|**Сжатых разностных групп строк**|Количество сжатых разностных групп строк.|  
|**Создано разностных групп строк**|Количество созданных разностных групп строк.|  
|**Коэффициент попаданий в кэш сегмента**|Процент сегментов столбцов, найденных в пуле columnstore без вызова операции чтения с диска.|  
|**Коэффициент попаданий в кэш сегмента — базовое значение**|Только для внутреннего применения.|
|**Операции чтения сегмента/c**|Количество физических операций чтения сегмента.|  
|**Всего перенесенных буферов удаления**|Количество очисток буфера удаления при выполнении задачи переноса кортежей.|  
|**Всего оценок политики слияния**|Количество оценок политики слияния для columnstore.|  
|**Всего сжатых групп строк**|Общее количество сжатых групп строк.|  
|**Всего групп строк, подходящих для слияния**|Число исходных групп строк, подходящих для слияния с момента запуска SQL Server.|  
|**Всего групп строк, сжатых при слиянии**|Количество сжатых групп конечных строк, созданных с помощью операции MERGE после запуска SQL Server.|  
|**Всего слито исходных групп строк**|Количество исходных групп строк, слитых после запуска SQL Server.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
