---
title: "Восстановление по журналу после сбоя экземпляра отказоустойчивого кластера | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: failover-clusters
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
caps.latest.revision: "31"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1f13897f5d754bc8d6b65034f0c9aab842b31c7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="recover-from-failover-cluster-instance-failure"></a>Восстановление по журналу после сбоя экземпляра отказоустойчивого кластера
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается восстановление кластера с помощью оснастки "Диспетчер отказоустойчивости кластеров" после отработки отказа в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Оснастка «Диспетчер отказоустойчивости кластеров» — это приложение управления кластером для службы WSFC.  
  
-   [Восстановление после неустранимого сбоя](#Scenario1)  
  
-   [Восстановление после программного сбоя](#Scenario2)  
  
##  <a name="Scenario1"></a> Восстановление после неустранимого сбоя  
 Для восстановления после неустранимого сбоя выполните следующие действия. Причина могла, например, заключаться в неисправности дискового контроллера или сбое операционной системы. В данном случае в кластере, состоящем из двух узлов, сбой вызван отказом оборудования в узле 1.  
  
1.  После сбоя на узле 1 отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI переключается на узел 2.  
  
2.  Исключите узел 1 из FCI. Для этого откройте оснастку "Диспетчер отказоустойчивости кластеров" из узла 2, щелкните правой кнопкой узел 1, выберите пункт **Действия перемещения**, а затем выберите команду **Исключить узел**.  
  
3.  Проверьте, исключен ли узел 1 из определения кластера.  
  
4.  Установите новое оборудование взамен отказавшего в узле 1.  
  
5.  При помощи оснастки «Диспетчер отказоустойчивости кластеров» добавьте к существующему кластеру узел 1. Дополнительные сведения см. в статье [Подготовка к установке отказоустойчивого кластера](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
6.  Убедитесь, что учетные записи администраторов одинаковы на всех узлах кластера.  
  
7.  Запустите программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чтобы добавить узел 1 к FCI. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
##  <a name="Scenario2"></a> Восстановление после устранимого сбоя  
 Для восстановления после устранимого сбоя выполните следующие действия. В данном случае причиной сбоя является узел 1, неработающий или находящийся вне сети, но не поврежденный полностью. Это может вызываться ошибкой операционной системы, отказом оборудования или сбоем в самом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
1.  После сбоя на узле 1 FCI переключается на узел 2.  
  
2.  Разрешите проблему на узле 1.  
  
3.  Убедитесь, что все узлы находятся в режиме «в сети» и работает служба WSFC.  
  
4.  Переведите [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на восстановленный узел.  
  
  
