---
title: "Высокий уровень доступности (службы Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "высокий уровень доступности [SQL Server], службы Reporting Services"
  - "высокий уровень доступности [службы Reporting Services]"
  - "службы Reporting Services, высокий уровень доступности"
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# Высокий уровень доступности (службы Reporting Services)
  Сервер отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является сервером без сохранения состояния, на котором в двух реляционных базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранятся данные приложений, содержимое, свойства и сведения о сеансах. Лучшим способом обеспечить доступность функций служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] будут следующие действия.  
  
-   Используйте функцию высокого уровня доступности компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , чтобы максимально увеличить время работоспособности баз данных сервера отчетов. Если экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] настроить для работы в отказоустойчивом кластере, при создании базы данных сервера отчетов можно выбрать этот экземпляр.  
  
-   Для баз данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и для источников данных по возможности используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. Дополнительные сведения см. в статье [Службы Reporting Services с группами доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Настройте несколько серверов отчетов для работы в режиме масштабного развертывания, где все серверы совместно используют одну базу данных сервера отчетов. Развертывание нескольких экземпляров сервера отчетов в масштабном развертывании (предпочтительно на разных серверах) помогает обеспечить непрерывную работу служб в случае отказа одного из экземпляров сервера.  
  
 Масштабное развертывание обеспечивает совместное использование базы данных. Если происходит отказ одного из серверов отчетов, остальные серверы в развертывании продолжают работать.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не имеет ограничений на кластеризацию. Само по себе масштабное развертывание не обеспечивает балансировки нагрузки, оно не определяет рабочую нагрузку сервера отчетов и не перенаправляет запросы на обработку на менее загруженный сервер. Оно не перенаправляет на обработку запросы, не завершенные вследствие ошибки. Чтобы получить возможность балансировать нагрузку, необходимо настроить балансирование нагрузки на веб-серверах, на которых находятся серверы отчетов, а затем настроить серверы отчетов для работы в режиме масштабного развертывания, чтобы они использовали одну базу данных сервера отчетов.  
  
 Веб-служба сервера отчетов и служба Windows тесно интегрируются и выполняются вместе как один экземпляр сервера отчетов. Нельзя настроить доступность одного сервера отдельно от другого.  
  
## См. также  
 [Решения высокого уровня доступности (SQL Server)](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Масштабное развертывание — основной режим служб Reporting Services (диспетчер конфигурации)](../Topic/Scale-out%20Deployment%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)  
  
  