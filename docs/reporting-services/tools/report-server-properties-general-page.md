---
title: Свойства сервера (страница "Общие") | Документы Майкрософт
ms.date: 06/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 71c0d3d28de1a9c63770b37f2bb6013768aaee78
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65576168"
---
# <a name="report-server-properties-general-page"></a>Свойства сервера отчетов (страница "Общие")
  Данная страница позволяет просмотреть или изменить заголовок, используемый в диспетчере отчетов, включить или отключить папку «Мои отчеты», выбрать определение роли для защиты папки «Мои отчеты», а также включить или отключить клиентское средство управления печатью.  
  
 **Чтобы открыть эту страницу:**
 1) Запуск [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Подключитесь к экземпляру сервера отчетов.
 3) Щелкните имя сервера отчетов правой кнопкой мыши и выберите пункт **Свойства**.  
  
 Свойства сервера, для которых доступна настройка, определяются режимом сервера. Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, то включить папку "Мои отчеты" или установить заголовок приложения для веб-портала нельзя.  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Введите имя, которое будет отображаться в веб-портале. Значение по умолчанию — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Указанное имя отображается только в диспетчере отчетов.  
  
 **Версия**  
 Это свойство доступно только для чтения. Позволяет указать используемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **Выпуск**  
 Это свойство доступно только для чтения. Задает текущий экземпляр сервера отчетов. Диспетчер отчетов имеется не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Выпуски и поддерживаемые функции SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
 **Режим проверки подлинности**  
 Это свойство доступно только для чтения. Оно определяет типы запросов на проверку подлинности, принимаемые экземпляром сервера отчетов. Чтобы изменить режим проверки подлинности, необходимо изменить файл **RSReportServer.config** . Дополнительные сведения см. в статье [Authentication with the Report Server](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 **URL-адрес**  
 Это свойство доступно только для чтения. Задает URL-адрес для веб-службы сервера отчетов. Это значение указывается в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Включить папку «Мои отчеты» для каждого пользователя**  
 Папка **Мои отчеты** становится доступной для пользователей. Этот параметр доступен только при работе с серверами отчетов в собственном режиме.  
  
 **Выбрать роль, которая будет применяться к каждой папке «Мои отчеты»**  
 Задает определение роли для защиты папки «Мои отчеты». Это определение роли обозначает набор задач, которые поддерживаются во время работы в каждой папке «Мои отчеты».  

  
## <a name="see-also"></a>См. также:  
 [Установка свойств сервера отчетов (среда Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Включение и отключение папки "Мои отчеты"](../../reporting-services/report-server/enable-and-disable-my-reports.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Защита рабочего пространства "Мои отчеты"](../../reporting-services/security/secure-my-reports.md)  
  
  

