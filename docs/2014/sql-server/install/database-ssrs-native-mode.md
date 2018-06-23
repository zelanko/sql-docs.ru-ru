---
title: Базы данных (собственный режим SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 4c8ff22e9edee8af2af4b948289b56c3078e4232
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098359"
---
# <a name="database-ssrs-native-mode"></a>База данных (службы Reporting Services в собственном режиме)
  Страница «База данных» используется для создания и настройки баз данных сервера отчетов, предназначенных для внутреннего хранения одного или нескольких экземпляров сервера отчетов. При настройке сервера отчетов для использования удаленного сервера отчетов, необходимо использовать [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager для создания базы данных.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
 Создание базы данных сервера отчетов и настройка подключения представляет собой многоэтапный процесс. Данная страница содержит мастера для каждого типа задач. В процессе настройки создаются или обновляются разрешения и имена входа. Каждый шаг можно отслеживать на странице «Выполнение». В случае возникновения ошибки можно просмотреть сведения об ее устранении.  
  
 Базой данных сервера отчетов должен поддерживаться определенный режим сервера. Режимом по умолчанию является собственный режим, но можно также создать базу данных сервера отчетов для работы в режиме интеграции с SharePoint, если сервер отчетов используется в крупномасштабном развертывании продукта или технологии SharePoint. Дополнительные сведения см. в разделе [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигураций служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager и нажмите кнопку **базы данных** в области навигации. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Имя SQL Server**  
 В текущей базе данных сервера отчетов **имя SQL Server** указывает имя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором запущена база данных сервера отчетов. Можно использовать экземпляр по умолчанию или именованный экземпляр на локальном или удаленном компьютере.  
  
 **Database Name**  
 Позволяет указать имя базы данных сервера отчетов, в которой хранятся серверные данные.  
  
 **Режим сервера отчетов**  
 Указывает на то, поддерживается ли базой данных сервера отчетов собственный режим или режим интеграции с SharePoint. Дополнительные сведения см. в разделе [сервера отчетов служб Reporting Services](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Изменение базы данных**  
 Запуск пошагового мастера необходим для создания или выбора базы данных сервера отчетов.  
  
 **Тип учетных данных**  
 Позволяет задать учетные данные, используемые сервером отчетов для соединения со своей базой данных. Следующие типы учетных данных, можно указать учетную запись службы, пользователя домена Windows, локальный пользователь Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа базы данных. Дополнительные сведения о выборе учетных данных см. в разделе [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Имя пользователя**  
 Указывает учетную запись пользователя домена, если используются учетные данные Windows, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа. Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетные данные. Если вы используете учетные данные Windows, укажите их в следующем формате:  *\<домена >\\< учетная запись\>*.  
  
 **Пароль**  
 Позволяет задать пароль для учетной записи.  
  
 **Изменение учетных данных**  
 Запуск пошагового мастера необходим для выбора различных учетных записей или обновления пароля учетной записи, которая используется для соединения с базой данных сервера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Разделы справки F1 по диспетчеру конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  