---
title: Объект метаданных каталога (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 84a8e5324d5dcb1f2727fbc73d3a9c1f75fda618
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558371"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, объект метаданных каталога
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Объект производительности **SQLServer:Catalog Metadata** предоставляет счетчики для метаданных каталога SQL Server.

В следующей таблице представлены объекты производительности **Catalog Metadata** SQL Server.


|**Счетчики метаданных каталога для SQL Server**|Описание|  
|-------------|-----------------|  
|**Кол-во записей кэша**|Количество записей в кэше метаданных каталога.|
|**Прикреплено записей кэша**|Количество закрепленных записей в кэше метаданных каталога.|
|**Коэффициент попадания в кэш**|Соотношение между количеством попаданий в кэш метаданных каталога и количеством обращений к нему.|
|**Базовый коэффициент попаданий в кэш**|Только для внутреннего применения.|

Для каждой базы данных существует один экземпляр счетчика.

## <a name="see-also"></a>См. также:  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
