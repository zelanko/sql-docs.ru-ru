---
title: SQL Server, объект Cursor Manager by Type | Документация Майкрософт
description: Сведения об объекте SQLServer:Cursor Manager by Type, который содержит счетчики для отслеживания курсоров с группировкой по типу.
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
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 95f88849070d95703b611a00c5c1e5abef94fffb
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505798"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: объект Cursor Manager by Type
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект **SQLServer: диспетчер курсоров по типу** содержит счетчики для отслеживания курсоров с группировкой по типу.  
  
 Следующая таблица описывает счетчики SQL Server **диспетчер курсоров по типу** .  
  
|Счетчики «Cursor Manager by Type»|Описание|  
|-------------------------------------|-----------------|  
|**Активные курсоры**|Число активных курсоров.|  
|**Коэффициент попадания в кэш**|Соотношение между числом попаданий в кэш и числом уточняющих запросов.|  
|**Базовый коэффициент попаданий в кэш**|Только для внутреннего использования.| 
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
  
  
