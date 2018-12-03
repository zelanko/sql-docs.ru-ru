---
title: Объект метаданных каталога (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0474646ae51a8fdabe6ff139c6eff1ec966f8d93
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158812"
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
