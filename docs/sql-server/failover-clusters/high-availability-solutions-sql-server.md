---
title: "Решения высокого уровня доступности (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 05/19/2016
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
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
caps.latest.revision: "84"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7af2a4035d3c528189cca77a4506e98db1acd93c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="high-availability-solutions-sql-server"></a>Решения высокого уровня доступности (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В данном разделе представлены некоторые решения высокой доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], позволяющие повысить уровень доступности серверов или баз данных. Решения по повышению уровня доступности защищают от последствий ошибок в программах и сбоев оборудования, помогая сохранить доступность приложений, и предельно сокращают для пользователей время простоя.    
    
   
>  **Примечание.** Хотите узнать, какие выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживают определенное решение высокой доступности? См. подраздел "Высокий уровень доступности (всегда ВКЛ)" раздела [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).    
     
    
##  <a name="TermsAndDefinitions"></a> Общие сведения о решениях SQL Server с высоким уровнем доступности    
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет несколько вариантов обеспечения высокого уровня доступности сервера или базы данных. Существуют следующие режимы обеспечения высокого уровня доступности.    
    
*  Экземпляры отказоустойчивого кластера AlwaysOn    
 В рамках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn экземпляры отказоустойчивой кластеризации AlwaysOn используют функциональные возможности отказоустойчивой кластеризации Windows Server (WSFC) для обеспечения высокого уровня доступности локальных ресурсов за счет избыточности на уровне экземпляра сервера — *экземпляра отказоустойчивого кластера* (FCI). Экземпляр отказоустойчивого кластера (FCI) является единственным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленным на всех узлах отказоустойчивой кластеризации Windows Server (WSFC) и, возможно, в нескольких подсетях. Экземпляр отказоустойчивого кластера выглядит в сети как экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенный на одном компьютере, но экземпляр отказоустойчивого кластера обеспечивает отработку отказа с переходом одного узла WSFC на другой узел, если текущий узел становится недоступным.    
    
 Дополнительные сведения см. в разделе [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).    
    
*  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]    
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] — решение по обеспечению высокой доступности и аварийного восстановления на уровне предприятия, впервые введенное в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для повышения доступности одной или нескольких пользовательских баз данных. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] требует, чтобы экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] располагались на узлах отказоустойчивого кластера Windows Server (WSFC). Дополнительные сведения см. в разделе [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).    
    
  
>  **Примечание.** Экземпляр отказоустойчивого кластера (FCI) может эффективно использовать [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] для выполнения удаленного аварийного восстановления на уровне базы данных. Дополнительные сведения см. в разделе [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).    
    
*  Зеркальное отображение базы данных. **Примечание.** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо нее рекомендуется пользоваться представлением [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .     
Зеркальное отображение базы данных — это решение, предназначенное главным образом для увеличения доступности базы данных за счет почти мгновенного перехода на отработку отказа. Зеркальное отображение базы данных может использоваться для поддержки одиночной резервной базы данных или *зеркальной базы данных*, соответствующей базе данных, которая доступна для чтения и записи и называется *основной базой данных*. Дополнительные сведения см. в разделе [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md).    
    
*  доставка журналов;    
 Подобно [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] и зеркальному отображению базы данных, доставка журналов функционирует на уровне базы данных. Доставку журналов можно использовать для поддержки одной или нескольких баз данных "горячего" резервирования (которые называются *базами данных-получателями*) для единой рабочей базы данных, называемой *базой данных-источником*. Дополнительные сведения о доставке журналов см. в разделе [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md).    
    
##  <a name="RecommendedSolutions"></a> Рекомендуемые решения для использования SQL Server в целях защиты данных    
 Рекомендации для обеспечения защиты данных в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :    
    
-   Для защиты данных посредством решения общего диска сторонних разработчиков (SAN) рекомендуется использовать экземпляры отказоустойчивой кластеризации AlwaysOn.    
    
-   Для защиты данных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]рекомендуется использовать [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].    
    
       >  При использовании выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который не поддерживает [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], рекомендуется применять доставку журналов. Сведения о выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поддерживающих [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], см. в подразделе "Высокий уровень доступности (AlwaysOn)" раздела [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).    
    
## <a name="see-also"></a>См. также:    
 [Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)     
 [Зеркальное отображение базы данных: взаимодействие и сосуществание (SQL Server)](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md)     
 [Нерекомендуемые функции ядра СУБД в SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)    
    
  

