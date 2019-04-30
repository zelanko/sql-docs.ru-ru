---
title: Мастер изменения учетных данных (собственный режим служб SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 632cfe6f1ea61612f59225f38a665ef73da0d898
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215119"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Мастер изменения учетных данных (службы Reporting Services в собственном режиме)
  В диспетчере конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] имеется мастер изменения учетных данных, помогающий выполнить шаги по изменению учетной записи, используемой сервером отчетов для подключения к базе данных сервера отчетов. Когда учетные данные изменены, диспетчер конфигурации обновляет на сервере баз данных все разрешения и сведения о регистрации в базе данных для базы данных сервера отчетов, активно используемой сервером отчетов.  
  
 Чтобы запустить этот мастер, в диспетчере конфигурации служб **на странице базы данных нажмите кнопку** Изменить учетные данные [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Инструкции по запуску [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, см. в разделе [диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
## <a name="options"></a>Параметры  
 **Сервер базы данных**  
 Определяет имя экземпляра компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором запущена база данных сервера отчетов.  
  
 При подключении к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] следует пользоваться учетными данными, имеющими разрешение на вход на сервер и обновление данных в базе данных. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует учетные данные текущего пользователя Windows, но при отсутствии имени входа или разрешения на доступ к базе данных можно указать имя входа в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Другие учетные данные Windows указать нельзя. Если подключение необходимо производить от лица другого пользователя Windows, то следует войти от этого пользователя, а затем запустить диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Учетные данные**  
 Задает учетную запись, используемую сервером отчетов для подключения к базе данных сервера отчетов. В качестве этого значения допускается указывать учетную запись веб-службы сервера отчетов, имя входа базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , определенное в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором размещен сервер отчетов, или учетную запись Windows. Если вы используете учетную запись Windows, можно указать локальную учетную запись (*\<имя_компьютера >\\< имя пользователя\>*) Если сервер отчетов и базы данных находятся на том же компьютере или пользователя домена Учетная запись (*\<домена >\\< имя пользователя\>*), если они находятся на разных компьютерах в одном домене.  
  
 Сервер отчетов создаст имя входа базы данных и присвоит для указанной учетной записи разрешения базы данных.  
  
 Сервер отчетов не создает саму учетную запись. Указанная учетная запись уже должна быть создана и доступна для текущей конфигурации развертывания. В частности, если при использовании учетной записи Windows база данных находится на удаленном компьютере, следует указывать учетную запись, имеющую разрешения для этого компьютера.  
  
 Если компьютер находится в другом домене или в недоверенном домене, то лучше пользоваться именем входа базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о выборе учетной записи, см. в разделе [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Сводка**  
 Прежде чем запускать мастер, проверьте настройки.  
  
 **Ход выполнения и завершение**  
 Проследите за ходом выполнения каждой из задач.  
  
## <a name="see-also"></a>См. также  
 [База данных &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Мастер изменения базы данных &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Разделы справки F1 диспетчера конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
