---
title: PowerPivot для SharePoint (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef00476e7c469a98532e58302c560c805669421d
ms.sourcegitcommit: 7183735e38dd94aa3b9bab2b73ccab54c916ff86
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683589"
---
# <a name="powerpivot-for-sharepoint-ssas"></a>PowerPivot для SharePoint (SSAS)
  PowerPivot для SharePoint — это сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], исполняемый в режиме интеграции с SharePoint. PowerPivot для SharePoint предусматривает размещение данных PowerPivot на сервере в ферме SharePoint. Данные PowerPivot представляют собой модель аналитических данных, которая создается в одной из следующих программ:  
  
-   Надстройка PowerPivot для Excel 2010  
  
-   Excel 2013  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010  
  
 Для размещения этих данных на сервере требуются SharePoint, службы Excel и установка компонента PowerPivot для SharePoint. Данные загружаются в экземпляры PowerPivot для SharePoint, где их можно обновлять по расписанию с помощью функции обновления данных PowerPivot, предоставлямой сервером для книг Excel 2010 или службами Excel в SharePoint 2013 для книг Excel 2013.  
  
## <a name="powerpivot-for-sharepoint-2013"></a>PowerPivot для SharePoint 2013  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] поддерживает [!INCLUDE[msCoName](../../includes/msconame-md.md)] использование служб Excel SharePoint 2013 книги Excel, содержащие модели данных и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчеты Power View.  
  
 Службы Excel в SharePoint 2013 включают функции модели данных для обеспечения взаимодействия с книгой PowerPivot в браузере. Не обязательно развертывать отдельную надстройку PowerPivot для SharePoint 2013 в ферме. Достаточно установить сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint и зарегистрировать сервер в параметрах **Модель данных** служб Excel.  
  
 Развернув надстройку PowerPivot для SharePoint 2013, можно полностью задействовать функциональность и компоненты PowerPivot в ферме SharePoint. Дополнительные возможности включают коллекцию PowerPivot, обновления данных расписания и панели управления PowerPivot.  
  
 ![Развертывание сервера в режиме служб SSAS PowerPivot 2](../media/as-powerpivot-mode-2server-deployment.gif "Развертывание сервера в режиме служб SSAS PowerPivot 2")  
  
## <a name="powerpivot-for-sharepoint-2010"></a>PowerPivot для SharePoint 2010  
 PowerPivot для SharePoint 2010 предусматривает размещение данных PowerPivot на сервере в ферме SharePoint 2010. Данные PowerPivot представляют собой модель аналитических данных, которая создается в Excel с помощью надстройки «PowerPivot для Excel». Для размещения этих данных на сервере требуются SharePoint 2010, службы Excel и компонент PowerPivot для SharePoint. Данные загружаются в экземпляры PowerPivot для SharePoint в ферме, где их можно обновлять с запланированными интервалами с помощью функции обновления данных PowerPivot, предоставляемой сервером.  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a>Компоненты PowerPivot для SharePoint 2010  
 Компонент PowerPivot для SharePoint реализован в виде общей службы. Это означает, что для администрирования, обеспечения безопасности и использования приложения службы PowerPivot можно использовать встроенные функции и инфраструктуру. Обнаружение серверов и баз данных, перенаправление и управление соединениями осуществляются на уровне фермы. Центр администрирования предоставляет административный интерфейс для служб, которые используются для управления удостоверениями, состоянием и свойствами конфигурации сервера.  
  
 Полное развертывание PowerPivot для SharePoint включает клиентские и серверные компоненты, которые интегрируются с Excel и службами Excel в ферме SharePoint. Данные PowerPivot в книге Excel представляют собой базу данных служб Analysis Services, для которой требуется подсистема аналитики в памяти xVelocity (VertiPaq) для загрузки и запросов данных. На клиентской рабочей станции компонент xVelocity выполняется внутри процессов в Excel. В ферме SharePoint службы Analysis Services работают на сервере приложений, где они связаны с другими службами, которые выполняют обработку запросов данных PowerPivot. На приведенной ниже диаграмме показаны клиентские и серверные компоненты PowerPivot.  
  
 ![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")  
  
 Веб-служба PowerPivot выполняется на сервере веб-приложений. Она направляет запросы из веб-приложения на экземпляр системной службы PowerPivot в ферме.  
  
 Системная служба PowerPivot выдает запросы на загрузку для сервера служб Analysis Services и управляет текущими соединениями с данными, которые уже загружены в память, а также кэширует или выгружает данные, если они больше не используются или возникают конфликты из-за системных ресурсов. Она также отслеживает активность пользователей. Данные об исправности сервера и другие данные об использовании собираются и предоставляются в отчетах, позволяющих оценить, насколько хорошо работает система.  
  
 Завершает развертывание экземпляр сервера служб Analysis Service в режиме интеграции с SharePoint. Он загружает и выгружает данные и управляет запросами к ним. Он также обрабатывает данные, если для книги настроено обновление данных PowerPivot.  Каждый экземпляр тесно связан с локальной системной службой PowerPivot, которая входит в состав той же установки.  
  
##  <a name="bkmk_RelatedContent"></a>В этом разделе  
 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [Средства настройки PowerPivot](power-pivot-configuration-tools.md)  
  
 [Аутентификация и авторизация PowerPivot](power-pivot-authentication-and-authorization.md)  
  
 [Правила определения исправности PowerPivot — настройка](configure-power-pivot-health-rules.md)  
  
 [Панель мониторинга управления PowerPivot и данные об использовании](power-pivot-management-dashboard-and-usage-data.md)  
  
 [Галерея PowerPivot](../../2014-toc/index.yml)  
  
 [Доступ к данным PowerPivot](power-pivot-data-access.md)  
  
 [Обновление данных PowerPivot](power-pivot-data-refresh.md)  
  
 [Веб-каналы данных PowerPivot](power-pivot-data-feeds.md)  
  
 [Соединение семантической модели бизнес-аналитики PowerPivot &#40;. BISM&#41;](power-pivot-bi-semantic-model-connection-bism.md)  
  
 **В других разделах**  
  
## <a name="additional-topics"></a>Дополнительные разделы  
 [PowerPivot для SharePoint обновления](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [Установка PowerPivot для SharePoint 2013](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [Примеры топологий и стоимости лицензий для SQL Server 2014 самостоятельной бизнес-аналитики](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a>См. также  
 [Планирование и развертывание PowerPivot](https://go.microsoft.com/fwlink/?linkID=220972)   
 [Аварийное восстановление в PowerPivot для SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
