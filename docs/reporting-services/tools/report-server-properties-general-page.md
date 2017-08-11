---
title: "Свойства сервера (страница «Общие») | Документы Microsoft"
ms.custom: 
ms.date: 06/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: dbd2d63c8698cb9e33361c12980aa6abdeaaae7b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-server-properties-general-page"></a>Свойства сервера отчетов (страница «Общие»)
  Данная страница позволяет просмотреть или изменить заголовок, используемый в диспетчере отчетов, включить или отключить папку «Мои отчеты», выбрать определение роли для защиты папки «Мои отчеты», а также включить или отключить клиентское средство управления печатью.  
  
 **Чтобы открыть эту страницу:**
 1) Запуск [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Подключитесь к экземпляру сервера отчетов.
 3) Щелкните имя сервера отчетов правой кнопкой мыши и выберите пункт **Свойства**.  
  
 Свойства сервера, для которых доступна настройка, определяются режимом сервера. Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, то включить папку "Мои отчеты" или установить заголовок приложения для веб-портала нельзя.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите имя, которое будет отображаться в веб-портале. По умолчанию это значение служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Указанное имя отображается только в диспетчере отчетов.  
  
 **Версия**  
 Это свойство предназначено только для чтения. Задает используемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Выпуск**  
 Это свойство предназначено только для чтения. Задает текущий экземпляр сервера отчетов. Диспетчер отчетов имеется не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 **Режим проверки подлинности**  
 Это свойство предназначено только для чтения. Оно определяет типы запросов на проверку подлинности, принимаемые экземпляром сервера отчетов. Чтобы изменить режим проверки подлинности, необходимо изменить файл **RSReportServer.config** . Дополнительные сведения см. в статье [Authentication with the Report Server](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 **URL-адрес**  
 Это свойство предназначено только для чтения. Задает URL-адрес для веб-службы сервера отчетов. Это значение указывается в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Включить папку «Мои отчеты» для каждого пользователя**  
 Папка **Мои отчеты** становится доступной для пользователей. Этот параметр доступен только при работе с серверами отчетов в собственном режиме.  
  
 **Выбрать роль, которая будет применяться к каждой папке «Мои отчеты»**  
 Задает определение роли для защиты папки «Мои отчеты». Это определение роли обозначает набор задач, которые поддерживаются во время работы в каждой папке «Мои отчеты».  

  
## <a name="see-also"></a>См. также раздел  
 [Настройка свойств сервера отчетов &#40; Среда Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Включение и отключение «Мои отчеты»](../../reporting-services/report-server/enable-and-disable-my-reports.md)   
 [Сервер отчетов в Справка F1 среды Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Защита рабочего пространства "Мои отчеты"](../../reporting-services/security/secure-my-reports.md)  
  
  


