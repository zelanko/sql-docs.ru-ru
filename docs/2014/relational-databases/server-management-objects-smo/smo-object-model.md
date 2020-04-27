---
title: Объектная модель объектов SMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 637c60fd6d7ba53087a145135d7152066983b644
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63130619"
---
# <a name="smo-object-model"></a>Объектная модель SMO
  Модель объектов SMO представляет собой иерархию объектов.  <xref:Microsoft.SqlServer.Management.Smo.Server> Объект является объектом верхнего уровня, а все объекты класса экземпляра находятся в <xref:Microsoft.SqlServer.Management.Smo.Server> объекте.  
  
 Класс <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> является классом верхнего уровня со своей собственной иерархией объектов.  <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> Объект представляет [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы и сетевые параметры, доступные через поставщик WMI.  
  
 Помимо объектов <xref:Microsoft.SqlServer.Management.Smo.Server> и <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, существует несколько служебных классов, представляющих задачи или операции, например <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Модель объектов SMO состоит из нескольких пространств имен. Дополнительные сведения см. в разделе [Пространства имен объектов SMO](smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>См. также  
 [Схема модели объектов SMO](smo-object-model-diagram.md)   
 [Пространства имен SMO](smo-object-model-namespaces.md)   
 [Основные понятия о поставщике WMI для управления конфигурацией](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
