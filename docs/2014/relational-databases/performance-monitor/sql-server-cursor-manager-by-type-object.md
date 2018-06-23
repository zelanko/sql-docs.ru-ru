---
title: SQL Server, объект Cursor Manager by Type | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f4d0b776422d9570b22e36382ebbc1c655c901e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098396"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: объект Cursor Manager by Type
  Объект **SQLServer: диспетчер курсоров по типу** содержит счетчики для отслеживания курсоров с группировкой по типу.  
  
 Следующая таблица описывает счетчики SQL Server **диспетчер курсоров по типу** .  
  
|Счетчики «Cursor Manager by Type»|Описание|  
|-------------------------------------|-----------------|  
|**Активные курсоры**|Число активных курсоров.|  
|**Коэффициент попадания в кэш**|Соотношение между числом попаданий в кэш и числом уточняющих запросов.|  
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
  
## <a name="see-also"></a>См. также  
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  