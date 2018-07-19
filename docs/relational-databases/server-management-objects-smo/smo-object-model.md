---
title: Объектная модель SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e3bc9ec53d5550f8671b7ac9bb786ae9d631f6df
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061990"
---
# <a name="smo-object-model"></a>Объектная модель SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Модель объектов SMO представляет собой иерархию объектов.  <xref:Microsoft.SqlServer.Management.Smo.Server> Является объектом верхнего уровня и все объекты экземпляров класса располагаются ниже <xref:Microsoft.SqlServer.Management.Smo.Server> объекта.  
  
 Класс <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> является классом верхнего уровня со своей собственной иерархией объектов.  <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> Представляет объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы и сетевые настройки, доступные через поставщик WMI.  
  
 Помимо объектов <xref:Microsoft.SqlServer.Management.Smo.Server> и <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, существует несколько служебных классов, представляющих задачи или операции, например <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Модель объектов SMO состоит из нескольких пространств имен. Дополнительные сведения см. в разделе [Пространства имен объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>См. также  
 [Диаграмма модели объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [Пространства имен объектов SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [Основные понятия о поставщике WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
