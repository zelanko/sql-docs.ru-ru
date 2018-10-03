---
title: Свойства сервера (страница "Общие") | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: af0db1ac3d03fa03ea7bb3267656597d164c5302
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222220"
---
# <a name="server-properties-general-page"></a>Свойства сервера (страница «Общие»)
  Данная страница позволяет просмотреть или изменить заголовок, используемый в диспетчере отчетов, включить или отключить папку «Мои отчеты», выбрать определение роли для защиты папки «Мои отчеты», а также включить или отключить клиентское средство управления печатью.  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключитесь к экземпляру сервера отчетов, щелкните правой кнопкой мыши имя сервера отчетов и затем выберите **свойства**.  
  
 Свойства сервера, для которых доступна настройка, определяются режимом сервера. Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, то включить папку «Мои отчеты» или установить заголовок приложения для диспетчера отчетов нельзя.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите имя приложения, которое отображается в диспетчере отчетов. По умолчанию это значение служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Указанное имя отображается только в диспетчере отчетов.  
  
 **Версия**  
 Это свойство доступно только для чтения. Задает используемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Выпуск**  
 Это свойство доступно только для чтения. Задает текущий экземпляр сервера отчетов. Диспетчер отчетов имеется не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Режим проверки подлинности**  
 Это свойство доступно только для чтения. Оно определяет типы запросов на проверку подлинности, принимаемые экземпляром сервера отчетов. Чтобы изменить режим проверки подлинности, необходимо изменить файл RSReportServer.config. Дополнительные сведения см. в статье [Authentication with the Report Server](../security/authentication-with-the-report-server.md).  
  
 **URL-адрес**  
 Это свойство доступно только для чтения. Задает URL-адрес для веб-службы сервера отчетов. Это значение указывается в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Включить папку «Мои отчеты» для каждого пользователя**  
 Папка «Мои отчеты» становится доступной для пользователей. Этот параметр доступен только при работе с серверами отчетов в собственном режиме.  
  
 **Выбрать роль, которая будет применяться к каждой папке «Мои отчеты»**  
 Задает определение роли для защиты папки «Мои отчеты». Это определение роли обозначает набор задач, которые поддерживаются во время работы в каждой папке «Мои отчеты».  
  
 **Разрешить загрузку элемента управления печатью ActiveX клиента**  
 Наборы `EnableClientPrinting` системному свойству сервера отчетов. Если клиентская печать разрешена, у пользователей, имеющих разрешения локального администратора, имеется возможность загрузки подписанного элемента управления ActiveX для печати HTML-отчетов. Дополнительные сведения см. в разделе [Включение и отключение печати на стороне клиента для служб Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
## <a name="see-also"></a>См. также  
 [Установка свойств сервера отчетов (среда Management Studio)](set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Включение и отключение папки "Мои отчеты"](../report-server/enable-and-disable-my-reports.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Защита рабочего пространства "Мои отчеты"](../security/secure-my-reports.md)  
  
  
