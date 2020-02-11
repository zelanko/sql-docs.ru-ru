---
title: SQL Server, объект Cursor Manager by Type | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 35fa15dc6651d8bfd9b6d32cafd00cd47698560b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206971"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: объект Cursor Manager by Type
  Объект **SQLServer: диспетчер курсоров по типу** содержит счетчики для отслеживания курсоров с группировкой по типу.  
  
 Следующая таблица описывает счетчики SQL Server **диспетчер курсоров по типу** .  
  
|Счетчики «Cursor Manager by Type»|Description|  
|-------------------------------------|-----------------|  
|**Активные курсоры**|Число активных курсоров.|  
|**Коэффициент попадания в кэш**|Соотношение между числом попаданий в кэш и числом уточняющих запросов.|  
|**Число кэшированных курсоров**|Число курсоров данного типа, находящихся в кэше.|  
|**Счетчик использований кэша курсоров/с**|Число использований курсоров каждого из типов.|  
|**Использование памяти курсором**|Объем памяти (в килобайтах), занятый курсорами.|  
|**Запросов курсоров/с**|Число запросов SQL на курсоры, полученных сервером.|  
|**Использование рабочей таблицы курсора**|Число рабочих таблиц, занятых курсорами.|  
|**Число активных планов курсоров**|Число планов курсоров.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр диспетчера курсоров|Description|  
|-----------------------------|-----------------|  
|**_Total**|Сведения обо всех курсорах.|  
|**Курсор API**|Только сведения об API курсора.|  
|**Глобальный курсор TSQL**|Только сведения о глобальных курсорах [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**Локальный курсор TSQL**|Только сведения о локальных курсорах [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)  
  
  
