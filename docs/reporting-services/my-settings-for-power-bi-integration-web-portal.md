---
title: Мои параметры для интеграции с Power BI (веб-портал) | Документы Майкрософт
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7535b16e731bc74df98f853156214abcfbe5961f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65503719"
---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>Страница "Мои параметры", используемая для интеграции с Power BI (диспетчер отчетов)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

На странице **Мои параметры** в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] отдельные пользователи могут управлять входом с использованием [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Во время закрепления элемента отчета будет автоматически предложено войти в систему.  Однако если требуется выполнить вход вручную или выйти из системы, можно использовать страницу **Мои параметры** .  Если параметр меню **Мои параметры** не отображается, сервер отчетов не интегрирован с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>Зачем входить в систему

 При входе устанавливается связь между учетной записью пользователя [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и учетной записью [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  Кроме того, при этом создается маркер безопасности, который действителен в течение 90 дней. Если на момент истечения срока действия маркера к Power BI будут прикреплены какие-то элементы, отобразится уведомление.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
Плитки в панели мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] не будут обновляться, пока вы не выполните вход через **Мои параметры**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Как только вы выполните вход, будет создан новый маркер безопасности.  Плитки на информационной панели начнут обновляться по ранее настроенному расписанию.  

## <a name="next-steps"></a>Дальнейшие действия

[Интеграция с сервером отчетов Power BI](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Закрепление элементов служб Reporting Services на информационных панелях Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Панели мониторинга в Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Веб-портал](../reporting-services/web-portal-ssrs-native-mode.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
