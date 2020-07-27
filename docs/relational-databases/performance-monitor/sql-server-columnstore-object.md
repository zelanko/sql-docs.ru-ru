---
title: SQL Server, объект Columnstore | Документация Майкрософт
description: Сведения об объекте SQLServer:Columnstore, который предоставляет счетчики для наблюдения за выполнением индекса columnstore в SQL Server.
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f00f4405144cec17b0b0266308ebc6df39336a70
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458423"
---
# <a name="sql-server-columnstore-object"></a>SQL Server, объект Columnstore
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Объект **SQLServer:Columnstore** предоставляет счетчики для наблюдения за выполнением индекса columnstore в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В приведенной ниже таблице описываются счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Columnstore**.  
  
|Счетчики Columnstore|Описание|  
|--------------------------|-----------------|  
|**Закрыто разностных групп строк**|Количество закрытых разностных групп строк.|  
|**Сжатых разностных групп строк**|Количество сжатых разностных групп строк.|  
|**Создано разностных групп строк**|Количество созданных разностных групп строк.|  
|**Коэффициент попаданий в кэш сегмента**|Процент сегментов столбцов, найденных в пуле columnstore без вызова операции чтения с диска.|  
|**Коэффициент попаданий в кэш сегмента — базовое значение**|Только для внутреннего использования.|
|**Операции чтения сегмента/c**|Количество физических операций чтения сегмента.|  
|**Всего перенесенных буферов удаления**|Количество очисток буфера удаления при выполнении задачи переноса кортежей.|  
|**Всего оценок политики слияния**|Количество оценок политики слияния для columnstore.|  
|**Всего сжатых групп строк**|Общее количество сжатых групп строк.|  
|**Всего групп строк, подходящих для слияния**|Число исходных групп строк, подходящих для слияния с момента запуска SQL Server.|  
|**Всего групп строк, сжатых при слиянии**|Количество сжатых групп конечных строк, созданных с помощью операции MERGE после запуска SQL Server.|  
|**Всего слито исходных групп строк**|Количество исходных групп строк, слитых после запуска SQL Server.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
