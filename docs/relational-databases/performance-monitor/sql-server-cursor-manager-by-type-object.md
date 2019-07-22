---
title: SQL Server, объект Cursor Manager by Type | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 712cc824e6faa834bd8d6023e4948e9e80dfabce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986702"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: объект Cursor Manager by Type
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
