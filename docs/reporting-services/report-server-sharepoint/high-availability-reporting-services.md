---
title: "Высокий уровень доступности в службах Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 4cac952300b83cd2ad568a8dc6900bcf74e6c5a6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="high-availability-in-sql-server-reporting-services"></a>Высокий уровень доступности в службах Reporting Services

Сервер отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является сервером без сохранения состояния, на котором в двух реляционных базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранятся данные приложений, содержимое, свойства и сведения о сеансах. Лучшим способом обеспечить доступность функций служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] будут следующие действия.  
  
-   Используйте функцию высокого уровня доступности компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , чтобы максимально увеличить время работоспособности баз данных сервера отчетов. Если экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] настроить для работы в отказоустойчивом кластере, при создании базы данных сервера отчетов можно выбрать этот экземпляр.  
  
-   Для баз данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и для источников данных по возможности используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. Дополнительные сведения см. в статье [Службы Reporting Services с группами доступности AlwaysOn](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Настройте несколько серверов отчетов для работы в режиме масштабного развертывания, где все серверы совместно используют одну базу данных сервера отчетов. Развертывание нескольких экземпляров сервера отчетов в масштабном развертывании (предпочтительно на разных серверах) помогает обеспечить непрерывную работу служб в случае отказа одного из экземпляров сервера.  
  
 Масштабное развертывание обеспечивает совместное использование базы данных. Если происходит отказ одного из серверов отчетов, остальные серверы в развертывании продолжают работать.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не имеет ограничений на кластеризацию. Само по себе масштабное развертывание не обеспечивает балансировки нагрузки, оно не определяет рабочую нагрузку сервера отчетов и не перенаправляет запросы на обработку на менее загруженный сервер. Оно не перенаправляет на обработку запросы, не завершенные вследствие ошибки. Чтобы получить возможность балансировать нагрузку, необходимо настроить балансирование нагрузки на веб-серверах, на которых находятся серверы отчетов, а затем настроить серверы отчетов для работы в режиме масштабного развертывания, чтобы они использовали одну базу данных сервера отчетов.  
  
 Веб-служба сервера отчетов и служба Windows тесно интегрируются и выполняются вместе как один экземпляр сервера отчетов. Нельзя настроить доступность одного сервера отдельно от другого.  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
