---
title: Задание параметра максимальной степени параллелизма для оптимальной производительности | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5483ee76ebf8de754682e2b2da3d75ed6f688a67
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952929"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Задание параметра максимальной степени параллелизма для оптимальной производительности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило определяет, является ли значение параметра максимальной степени параллелизма (MAXDOP) больше 8. Установка большего значения часто приводит к неэффективному расходованию ресурсов и снижению производительности.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Установите значение параметра максимальной степени параллелизма равным 8 или меньше с помощью хранимой процедуры sp_configure.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 329204 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
