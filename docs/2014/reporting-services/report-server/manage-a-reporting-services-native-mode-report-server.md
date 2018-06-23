---
title: Управление сервером отчетов служб Reporting Services в собственном режиме | Документы Майкрософт
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
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 63291b62b946e733dbcc48359b06e1f3e33abc15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087311"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a>Управление сервером отчетов служб Reporting Services в собственном режиме
  Этот раздел содержит описание процедур по настройке экземпляра сервера отчетов в собственном режиме с использованием диспетчера конфигурации служб Reporting Services.  
  
## <a name="in-this-section"></a>в этом разделе  
 Подразделы в этом разделе организованы по категориям, что упрощает поиск необходимых инструкций. Подразделы первого раздела содержат описания основных задач по настройке конфигурации сервера отчетов, работающего в собственном режиме. Подразделы второго раздела посвящены дополнительным параметрам конфигурации. Подразделы третьего раздела помогут выполнить настройку конфигурации сервера отчетов для работы в режиме интеграции с SharePoint.  
  
### <a name="basic-configuration"></a>Основная конфигурация  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 Представляет шаги запуска программы настройки служб Reporting Services.  
  
 [Настройка учетной записи службы &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 Объясняет, как задать учетную запись и пароль службы сервера отчетов.  
  
 [Регистрация имени участника-службы &#40;имени участника-службы&#41; для сервера отчетов](register-a-service-principal-name-spn-for-a-report-server.md)  
 Показывает, как вручную зарегистрировать имя участника-службы для сервера отчетов, который запускается от учетной записи пользователя домена в сети, где используется проверка подлинности по протоколу Kerberos.  
  
 [Настройка URL-адрес &#40;диспетчер конфигурации служб SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 Описывает, как назначить один или несколько URL-адресов для получения доступа к веб-службе сервера отчетов и к диспетчеру отчетов.  
  
 [Создание базы данных сервера отчетов собственный режим &#40;диспетчер конфигурации служб SSRS&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 Представляет шаги создания базы данных сервера отчетов. Этот шаг требуется для развертывания установки служб Reporting Services.  
  
### <a name="advanced-or-optional-configuration"></a>Дополнительные или необязательные параметры настройки  
 [Настройка масштабного развертывания сервера отчетов собственный режим &#40;диспетчер конфигурации служб SSRS&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Представляет шаги настройки нескольких серверов отчетов для совместного использования базы данных сервера отчетов.  
  
 [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Содержит шаги настройки сервера отчетов для доставки по электронной почте.  
  
 [настроить брандмауэр для доступа к серверу отчетов](configure-a-firewall-for-report-server-access.md)  
 Описывает, как открыть порты для передачи входящих запросов и ответов от сервера отчетов.  
  
 [Настройка сервера отчетов в собственном режиме для локального администрирования &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 Описывает дополнительные шаги, которые необходимо выполнить для соединения с сервером отчетов или диспетчером отчетов с помощью http://localhost.  
  
 [Настройка сервера отчетов для удаленного администрирования](configure-a-report-server-for-remote-administration.md)  
 Описывает, как настроить экземпляр удаленного сервера отчетов для удаленного соединения и настройки с другого компьютера.  
  
 [Включение и отключение компонентов Reporting Services](turn-reporting-services-features-on-or-off.md)  
 Объясняет, как удалить неиспользуемые компоненты после установки служб Reporting Services.  
  
 [Включите удаленный контроль ошибок &#40;службы Reporting Services&#41;](enable-remote-errors-reporting-services.md)  
 Поясняет, как задать свойства сервера на сервере отчетов для возвращения дополнительных сведений об условиях возникновения ошибок на удаленных серверах.  
  
## <a name="see-also"></a>См. также  
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Настройка и администрирование сервера отчетов (службы Reporting Services в режиме интеграции с SharePoint)](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  