---
title: Автономные базы данных с группами доступности AlwaysOn (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8226893f960bd0c1b64c589219121f323226766d
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768650"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Автономные базы данных с группами доступности AlwaysOn (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот раздел содержит сведения об использовании автономной базы данных с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **В этом разделе.**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением автономной базы данных в группу доступности убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре, на котором размещена реплика доступности. Дополнительные сведения см. в разделах [Параметр конфигурации сервера "проверка подлинности автономной базы данных"](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) и [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Contained Databases](../../../relational-databases/databases/contained-databases.md)  
  
  
