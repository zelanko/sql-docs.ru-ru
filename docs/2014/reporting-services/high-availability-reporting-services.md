---
title: Высокий уровень доступности (службы Reporting Services) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: e1d11b2b53499b12a6a8a7dca262bc26ae777825
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097873"
---
# <a name="high-availability-reporting-services"></a>Высокий уровень доступности (службы Reporting Services)
  Сервер отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] является сервером без сохранения состояния, на котором в двух реляционных базах данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хранятся данные приложений, содержимое, свойства и сведения о сеансах. Таким образом, лучшим способом обеспечить доступность [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] функциональность будет делать следующее:  
  
-   Используйте функции высокого уровня доступности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] чтобы максимально увеличить время работоспособности баз данных сервера отчетов. При настройке [!INCLUDE[ssDE](../includes/ssde-md.md)] экземпляра для работы в отказоустойчивом кластере, при создании базы данных сервера отчетов, можно выбрать этот экземпляр.  
  
-   Для баз данных [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и для источников данных по возможности используйте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)]. Дополнительные сведения см. в статье [Службы Reporting Services с группами доступности AlwaysOn (SQL Server)](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Настройте несколько серверов отчетов для работы в режиме масштабного развертывания, где все серверы совместно используют одну базу данных сервера отчетов. Развертывание нескольких экземпляров сервера отчетов в масштабном развертывании (предпочтительно на разных серверах) помогает обеспечить непрерывную работу служб в случае отказа одного из экземпляров сервера.  
  
 Масштабное развертывание обеспечивает совместное использование базы данных. Если происходит отказ одного из серверов отчетов, остальные серверы в развертывании продолжают работать.  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не имеет ограничений на кластеризацию. Само по себе масштабное развертывание не обеспечивает балансировки нагрузки, оно не определяет рабочую нагрузку сервера отчетов и не перенаправляет запросы на обработку на менее загруженный сервер. Оно не перенаправляет на обработку запросы, не завершенные вследствие ошибки. Чтобы получить возможность балансировать нагрузку, необходимо настроить балансирование нагрузки на веб-серверах, на которых находятся серверы отчетов, а затем настроить серверы отчетов для работы в режиме масштабного развертывания, чтобы они использовали одну базу данных сервера отчетов.  
  
 Веб-служба сервера отчетов и служба Windows тесно интегрируются и выполняются вместе как один экземпляр сервера отчетов. Нельзя настроить доступность одного сервера отдельно от другого.  
  
## <a name="see-also"></a>См. также  
 [Решения высокого уровня доступности (SQL Server)](../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Настройка масштабного развертывания сервера отчетов собственный режим &#40;диспетчер конфигурации служб SSRS&#41;](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  