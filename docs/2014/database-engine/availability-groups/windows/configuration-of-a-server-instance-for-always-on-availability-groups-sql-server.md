---
title: Настройка экземпляра сервера для Always On групп доступности (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3392e6189b687516e627d847acceedb165141117
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937005"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a>Настройка экземпляра сервера для групп доступности AlwaysOn (SQL Server)
  Этот раздел содержит сведения о требованиях к настройке экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для поддержки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  Важные сведения о предварительных требованиях и ограничениях [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для узлов с отказоустойчивой кластеризацией Windows Server (WSFC) и экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в статье [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a>Термины и определения  
  
 Решение по обеспечению высокой доступности и аварийного восстановления, заменяющее зеркальное отображение базы данных на уровне предприятия. *Группа доступности* поддерживает среду отработки отказа для дискретного набора пользовательских баз данных, известных как *базы данных доступности*, которые совместно выполняют переход на другой ресурс.  
  
 реплика доступности  
 Создание экземпляра группы доступности, которая размещена на определенном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и поддерживает локальную копию каждой базы данных доступности, входящей в группу доступности. Существует два типа реплик доступности: одна *первичная* и от одной до четырех *вторичных реплик*. Экземпляры сервера, на которых размещаются реплики доступности для данной группы доступности, должны размещаться на разных узлах одной кластеризации WSFC.  
  
 [Конечная точка зеркального отображения базы данных](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 Конечная точка — это объект SQL Server, позволяющий SQL Server обмениваться данными по сети. Для участия в зеркальном отображении базы данных и/или [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , экземпляр сервера требует наличия специальной, выделенной конечной точки. Все подключения зеркального отображения и групп доступности на экземпляре сервера используют одну конечную точку зеркального отображения базы данных. Эта точка является конечной точкой специального назначения. Она используется исключительно для приема подключений от других экземпляров сервера.  
  
##  <a name="to-configure-a-server-instance-to-support-alwayson-availability-groups"></a><a name="ConfigSI"></a>Настройка экземпляра сервера для поддержки группы доступности AlwaysOn  
 Для поддержки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]экземпляр сервера должен находиться на узле в отказоустойчивом кластере WSFC, в котором размещается группа доступности; для него должна быть включена поддержка [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и должна иметься конечная точка зеркального отображения базы данных.  
  
1.  Включите функцию «Группы доступности AlwaysOn» на всех экземплярах сервера, которые будут использоваться в одной или нескольких группах доступности. На данном экземпляре сервера может быть размещена только одна реплика доступности для данной группы доступности.  
  
2.  Убедитесь, что в экземпляре сервера есть конечная точка зеркального отображения базы данных.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
 **Включение функции «Группы доступности AlwaysOn»**  
  
-   [Включение и отключение групп доступности AlwaysOn (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Определение того, существует ли конечная точка зеркального отображения базы данных**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 **Создание конечной точки зеркального отображения базы данных**  
  
-   [Создание конечной точки зеркального отображения базы данных для группы доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Включение использования сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Обучающая серия AlwaysON — HADRON. использование пулов рабочих потоков для баз данных с HADRON](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Видеоролики**  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 2: создание критически важного решения по обеспечению высокого уровня доступности с использованием AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы**  
  
     [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [SQL Server &#40;конечной точки зеркального отображения базы данных&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Группы доступности AlwaysOn: взаимодействие (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация Windows Server &#40;&#41; WSFC с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Экземпляры отказоустойчивого кластера AlwaysOn](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
