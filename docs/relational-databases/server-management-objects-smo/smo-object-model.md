---
title: Объектная модель SMO | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b5b4e39f7338c83b3683502d919bec41df3cdf2e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="smo-object-model"></a>Объектная модель SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Модель объектов SMO представляет собой иерархию объектов.  <xref:Microsoft.SqlServer.Management.Smo.Server> Является объектом верхнего уровня и все объекты экземпляров класса располагаются ниже <xref:Microsoft.SqlServer.Management.Smo.Server> объекта.  
  
 Класс <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> является классом верхнего уровня со своей собственной иерархией объектов.  <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> Представляет [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службами и сетевыми настройками, доступных через поставщик WMI.  
  
 Помимо объектов <xref:Microsoft.SqlServer.Management.Smo.Server> и <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, существует несколько служебных классов, представляющих задачи или операции, например <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Модель объектов SMO состоит из нескольких пространств имен. Дополнительные сведения см. в разделе [Пространства имен объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Диаграмма модели объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [Пространства имен объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [Основные понятия о поставщике WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
