---
title: Автономные базы данных с группами доступности
description: Использование автономных баз данных с группами доступности Always On
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26e92d38188b02c5a2ce0025cc2d33fccc5c6728
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67988422"
---
# <a name="use-contained-databases-with-always-on-availability-groups"></a>Использование автономных баз данных с группами доступности Always On 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот раздел содержит сведения об использовании автономной базы данных с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением автономной базы данных в группу доступности убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре, на котором размещена реплика доступности. Дополнительные сведения см. в разделах [Параметр конфигурации сервера "проверка подлинности автономной базы данных"](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) и [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Автономные базы данных](../../../relational-databases/databases/contained-databases.md)  
  
  
