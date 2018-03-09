---
title: "Задание параметра максимальной степени параллелизма для оптимальной производительности | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 20adae41c9cb1913f9c03fa0e4c2257583743475
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Задание параметра максимальной степени параллелизма для оптимальной производительности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это правило определяет, превышает ли значение параметра максимальной степени параллелизма (MAXDOP) число 8. Установка большего значения часто приводит к неэффективному расходованию ресурсов и снижению производительности.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Установите значение параметра максимальной степени параллелизма равным 8 или меньше с помощью хранимой процедуры sp_configure.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 329204 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
