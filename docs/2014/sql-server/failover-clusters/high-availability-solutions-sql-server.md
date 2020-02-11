---
title: Решения высокого уровня доступности (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43727e0c7795fbd1f2f0c6a56693c2f06fdf4536
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63193043"
---
# <a name="high-availability-solutions-sql-server"></a>Решения высокого уровня доступности (SQL Server)
  В данном разделе представлены некоторые решения высокой доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , позволяющие повысить уровень доступности серверов или баз данных. Решения по повышению уровня доступности защищают от последствий ошибок в программах и сбоев оборудования, помогая сохранить доступность приложений, и предельно сокращают для пользователей время простоя.  
  
> [!NOTE]  
>  Сведения о том, какой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает данное решение для повышения уровня доступности, см. в подразделе "Высокий уровень доступности AlwaysOn" раздела [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
(#RecommendedSolutions)  
  
##  <a name="TermsAndDefinitions"></a>Обзор SQL Server решений с высоким уровнем доступности  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет несколько вариантов обеспечения высокого уровня доступности сервера или базы данных. Существуют следующие режимы обеспечения высокого уровня доступности.  
  
 Экземпляры отказоустойчивого кластера (режим AlwaysOn)  
 В рамках предложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn экземпляры отказоустойчивого кластера AlwaysOn используют функции отказоустойчивой кластеризации Windows Server (WSFC), чтобы обеспечить локальную высокую доступность с помощью избыточности на уровне экземпляра сервера — *экземпляра отказоустойчивого кластера* (FCI). Экземпляр отказоустойчивого кластера (FCI) является единственным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленным на всех узлах отказоустойчивой кластеризации Windows Server (WSFC) и, возможно, в нескольких подсетях. Экземпляр отказоустойчивого кластера выглядит в сети как экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенный на одном компьютере, но экземпляр отказоустойчивого кластера обеспечивает отработку отказа с переходом одного узла WSFC на другой узел, если текущий узел становится недоступным.  
  
 Дополнительные сведения см. в статье [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md).  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 
  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] — решение по обеспечению высокой доступности и аварийного восстановления на уровне предприятия, впервые введенное в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для повышения доступности одной или нескольких пользовательских баз данных. 
  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] требует, чтобы экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] располагались на узлах отказоустойчивого кластера Windows Server (WSFC). Дополнительные сведения см. в разделе [группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).  
  
> [!NOTE]  
>  Экземпляр отказоустойчивого кластера (FCI) может эффективно использовать [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] для выполнения удаленного аварийного восстановления на уровне базы данных. Дополнительные сведения см. в разделе [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
 Зеркальное отображение базы данных  
 > [!NOTE]  
>  
  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо нее рекомендуется пользоваться представлением [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .  
  
 Зеркальное отображение базы данных — это решение, предназначенное главным образом для увеличения доступности базы данных за счет почти мгновенного перехода на отработку отказа. Зеркальное отображение базы данных может использоваться для поддержки одиночной резервной базы данных или *зеркальной базы данных*, соответствующей базе данных, которая доступна для чтения и записи и называется *основной базой данных*. Дополнительные сведения см. в разделе [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 доставка журналов;  
 Подобно [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] и зеркальному отображению базы данных, доставка журналов функционирует на уровне базы данных. Доставку журналов можно использовать для поддержки одной или нескольких баз данных "горячего" резервирования (которые называются *базами данных-получателями*) для единой рабочей базы данных, называемой *базой данных-источником*. Дополнительные сведения о доставке журналов см. в разделе Сведения о доставке журналов(SQL Server).  
  
##  <a name="RecommendedSolutions"></a>Рекомендуемые решения для использования SQL Server для защиты данных  
 Рекомендации для обеспечения защиты данных в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключаются в следующем.  
  
-   Для защиты данных посредством решения диска совместного использования сторонних разработчиков (SAN) рекомендуется использовать экземпляры отказоустойчивой кластеризации AlwaysOn.  
  
-   Для защиты данных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]рекомендуется использовать [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
    > [!NOTE]  
    >  При использовании выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который не поддерживает [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], рекомендуется применить доставку журналов. Сведения о выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживающих [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], см. в подразделе "Высокий уровень доступности (AlwaysOn)" раздела [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также:  
 [Отказоустойчивая кластеризация Windows Server &#40;&#41; WSFC с SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Зеркальное отображение базы данных: взаимодействие и сосуществование &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md)   
 [Устаревшие функции компонента Database Engine в SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
