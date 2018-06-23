---
title: Мастер изменения учетных данных (собственный режим SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: c742a02d3accf2a51c2c31bac598064ca34f14c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188398"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Мастер изменения учетных данных (службы Reporting Services в собственном режиме)
  В диспетчере конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] имеется мастер изменения учетных данных, помогающий выполнить шаги по изменению учетной записи, используемой сервером отчетов для подключения к базе данных сервера отчетов. Когда учетные данные изменены, диспетчер конфигурации обновляет на сервере баз данных все разрешения и сведения о регистрации в базе данных для базы данных сервера отчетов, активно используемой сервером отчетов.  
  
 Чтобы запустить мастер, нажмите кнопку **изменить учетные данные** на странице базы данных в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Инструкции по запуску [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager в разделе [диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
## <a name="options"></a>Параметры  
 **Сервер базы данных**  
 Указывает имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляра, который выполняется в базе данных сервера отчетов.  
  
 Для подключения к [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляр, необходимо использовать учетные данные, которые имеют разрешение на вход на сервер и обновление данных базы данных. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager использует текущие учетные данные Windows, но если у вас разрешения имени входа или базы данных, можно указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа базы данных.  
  
 Другие учетные данные Windows указать нельзя. Если вы хотите подключиться от имени другого пользователя Windows, вход от имени этого пользователя, а затем запустите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 **Учетные данные**  
 Задает учетную запись, используемую сервером отчетов для подключения к базе данных сервера отчетов. Допустимые значения включают учетную запись службы сервера веб-службы отчетов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа базы данных, определенное для [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляра используется для размещения сервера отчетов или учетной записью Windows. Если вы используете учетную запись Windows, можно указать локальную учетную запись (*\<имя_компьютера >\\< имя_пользователя\>*) Если сервер отчетов и базы данных находятся на том же компьютере или пользователя домена Учетная запись (*\<домена >\\< имя_пользователя\>*), если они находятся на разных компьютерах, в том же домене.  
  
 Сервер отчетов создаст имя входа базы данных и присвоит для указанной учетной записи разрешения базы данных.  
  
 Сервер отчетов не создает саму учетную запись. Указанная учетная запись уже должна быть создана и доступна для текущей конфигурации развертывания. В частности, если при использовании учетной записи Windows база данных находится на удаленном компьютере, следует указывать учетную запись, имеющую разрешения для этого компьютера.  
  
 Если компьютер находится в другой, либо недоверенных доменов, рассмотрите возможность использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа базы данных. Дополнительные сведения о выборе учетной записи см. в разделе [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Сводка**  
 Прежде чем запускать мастер, проверьте настройки.  
  
 **Ход выполнения и завершение**  
 Проследите за ходом выполнения каждой из задач.  
  
## <a name="see-also"></a>См. также  
 [База данных &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Мастер изменения базы данных &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Разделы справки F1 по диспетчеру конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  