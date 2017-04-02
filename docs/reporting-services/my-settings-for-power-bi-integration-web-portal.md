---
title: "Страница &quot;Мои параметры&quot;, используемая для интеграции с Power BI (диспетчер отчетов) | Microsoft Docs"
ms.date: "05/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pbi"
  - "power bi"
  - "power bi integration"
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# Страница &quot;Мои параметры&quot;, используемая для интеграции с Power BI (диспетчер отчетов)
  На странице **Мои параметры** в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] отдельные пользователи могут управлять входом с использованием [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Во время закрепления элемента отчета будет автоматически предложено войти в систему.  Однако если требуется выполнить вход вручную или выйти из системы, можно использовать страницу **Мои параметры**.  Если параметр меню **Мои параметры** не отображается, сервер отчетов не интегрирован с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## Зачем входить в систему  
 При входе устанавливается связь между учетной записью пользователя [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и учетной записью [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Кроме того, при этом создается маркер безопасности, который действителен в течение 90 дней. Если на момент истечения срока действия маркера к Power BI будут прикреплены какие-то элементы, отобразится уведомление.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
Плитки в панели мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] не будут обновляться, пока вы не выполните вход через **Мои параметры**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Как только вы выполните вход, будет создан новый маркер безопасности.  Плитки на информационной панели начнут обновляться по ранее настроенному расписанию.  
  
## См. также  
 [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Закрепление элементов служб Reporting Services на информационных панелях Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
 [Панели мониторинга в Power BI](https://support.powerbi.com/knowledgebase/articles/424868-dashboards-in-power-bi)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
