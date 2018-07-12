---
title: Объектная модель SMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e31e4efa6ee0655d50567a7da73e85cc811c6692
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175871"
---
# <a name="smo-object-model"></a>Объектная модель SMO
  Модель объектов SMO представляет собой иерархию объектов.  <xref:Microsoft.SqlServer.Management.Smo.Server> Является объектом верхнего уровня и все объекты экземпляров класса располагаются ниже <xref:Microsoft.SqlServer.Management.Smo.Server> объекта.  
  
 Класс <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> является классом верхнего уровня со своей собственной иерархией объектов.  <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> Представляет объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы и сетевые настройки, доступные через поставщик WMI.  
  
 Помимо объектов <xref:Microsoft.SqlServer.Management.Smo.Server> и <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, существует несколько служебных классов, представляющих задачи или операции, например <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Модель объектов SMO состоит из нескольких пространств имен. Дополнительные сведения см. в разделе [Пространства имен объектов SMO](smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>См. также  
 [Диаграмма модели объектов SMO](smo-object-model-diagram.md)   
 [Пространства имен объектов SMO](smo-object-model-namespaces.md)   
 [Основные понятия о поставщике WMI для управления конфигурацией](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
