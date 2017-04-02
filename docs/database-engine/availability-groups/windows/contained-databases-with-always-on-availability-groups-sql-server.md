---
title: "Автономные базы данных с группами доступности AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Группы доступности [SQL Server], взаимодействие"
  - "автономная база данных, AlwaysOnAvailabilityGroups"
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 9
---
# Автономные базы данных с группами доступности AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Этот раздел содержит сведения об использовании автономной базы данных с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **В этом разделе.**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением автономной базы данных в группу доступности убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре, на котором размещена реплика доступности. Дополнительные сведения см. в разделах [Параметр конфигурации сервера "проверка подлинности автономной базы данных"](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) и [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Автономные базы данных](../../../relational-databases/databases/contained-databases.md)  
  
  