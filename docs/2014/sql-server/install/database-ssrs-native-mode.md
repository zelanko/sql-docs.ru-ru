---
title: База данных (собственный режим SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 7dff59c26c057caec1df1f5850be41dcc6f85711
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952308"
---
# <a name="database-ssrs-native-mode"></a>База данных (службы Reporting Services в собственном режиме)
  Страница «База данных» используется для создания и настройки баз данных сервера отчетов, предназначенных для внутреннего хранения одного или нескольких экземпляров сервера отчетов. При настройке сервера отчетов для использования удаленной базы данных сервера отчетов необходимо создать ее с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
 Создание базы данных сервера отчетов и настройка подключения представляет собой многоэтапный процесс. Данная страница содержит мастера для каждого типа задач. В процессе настройки создаются или обновляются разрешения и имена входа. Каждый шаг можно отслеживать на странице «Выполнение». В случае возникновения ошибки можно просмотреть сведения об ее устранении.  
  
 Базой данных сервера отчетов должен поддерживаться определенный режим сервера. Режимом по умолчанию является собственный режим, но можно также создать базу данных сервера отчетов для работы в режиме интеграции с SharePoint, если сервер отчетов используется в крупномасштабном развертывании продукта или технологии SharePoint. Дополнительные сведения см. в разделе [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигураций служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Для открытия данной страницы запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и нажмите кнопку **База данных** на панели навигации. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Имя SQL Server**  
 В текущей базе данных сервера отчетов параметр **Имя SQL Server** является именем компонента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором работает база данных сервера отчетов. Можно использовать экземпляр по умолчанию или именованный экземпляр на локальном или удаленном компьютере.  
  
 **Database Name**  
 Позволяет указать имя базы данных сервера отчетов, в которой хранятся серверные данные.  
  
 **Режим сервера отчетов**  
 Указывает на то, поддерживается ли базой данных сервера отчетов собственный режим или режим интеграции с SharePoint. Дополнительные сведения см. в разделе [Reporting Services сервера отчетов](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Изменить базу данных**  
 Запуск пошагового мастера необходим для создания или выбора базы данных сервера отчетов.  
  
 **Тип учетных данных**  
 Позволяет задать учетные данные, используемые сервером отчетов для соединения со своей базой данных. Возможно задать следующие типы учетных данных: учетная запись службы, пользователь домена Windows, локальный пользователь Windows или имя входа базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о выборе учетных данных см. [в разделе Настройка подключения к &#40;базе данных&#41;сервера отчетов SSRS Configuration Manager](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Имя пользователя**  
 Позволяет задать учетную запись пользователя домена (в случае использования учетных данных Windows) или имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (в случае использования учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ). Если используются учетные данные Windows, укажите их в следующем формате: *\<domain > \\ < Account @ no__t-3*.  
  
 **Пароль**  
 Позволяет задать пароль для учетной записи.  
  
 **Изменить учетные данные**  
 Запуск пошагового мастера необходим для выбора различных учетных записей или обновления пароля учетной записи, которая используется для соединения с базой данных сервера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Диспетчер конфигурации служб Reporting Services разделы &#40;справки F1 службы SSRS в&#41;основном режиме](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
