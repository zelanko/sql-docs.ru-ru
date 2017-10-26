---
title: "SQL Server, объект Cursor Manager by Type | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 800c82cf495aa64371b2ca15bcc2e8833b5fd87d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: объект Cursor Manager by Type
  Объект **SQLServer: диспетчер курсоров по типу** содержит счетчики для отслеживания курсоров с группировкой по типу.  
  
 Следующая таблица описывает счетчики SQL Server **диспетчер курсоров по типу** .  
  
|Счетчики «Cursor Manager by Type»|Описание|  
|-------------------------------------|-----------------|  
|**Активные курсоры**|Число активных курсоров.|  
|**Коэффициент попадания в кэш**|Соотношение между числом попаданий в кэш и числом уточняющих запросов.|  
|**Базовый коэффициент попаданий в кэш**|Только для внутреннего применения.| 
|**Счетчик кэшированных курсоров**|Число курсоров данного типа, находящихся в кэше.|  
|**Число использований кэша курсоров/с**|Число использований курсоров каждого из типов.|  
|**Использование памяти курсорами**|Объем памяти (в килобайтах), занятый курсорами.|  
|**Запрошенных курсоров/с**|Число запросов SQL на курсоры, полученных сервером.|  
|**Использование рабочих таблиц курсора**|Число рабочих таблиц, занятых курсорами.|  
|**Количество активных планов исполнения курсора**|Число планов курсоров.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр диспетчера курсоров|Описание|  
|-----------------------------|-----------------|  
|**_Total**|Сведения обо всех курсорах.|  
|**API Cursor**|Только сведения об API курсора.|  
|**TSQL Global Cursor**|Только сведения о глобальных курсорах [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**TSQL Local Cursor**|Только сведения о локальных курсорах [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  

