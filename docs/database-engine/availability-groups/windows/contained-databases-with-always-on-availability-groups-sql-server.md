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
ms.openlocfilehash: 58bbe0be8b2e139327605e674c580b7520b32af9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893189"
---
# <a name="use-contained-databases-with-always-on-availability-groups"></a>Использование автономных баз данных с группами доступности Always On 
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  Этот раздел содержит сведения об использовании автономной базы данных с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением автономной базы данных в группу доступности убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре, на котором размещена реплика доступности. Дополнительные сведения см. в разделах [Параметр конфигурации сервера "проверка подлинности автономной базы данных"](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) и [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Автономные базы данных](../../../relational-databases/databases/contained-databases.md)  
  
  
