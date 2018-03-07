---
title: "Диалоговое окно \"Подключение к базе данных служб Master Data Services\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c4c248076922acb7f503e208a9221ba99007cd9
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Диалоговое окно «Подключение к базе данных служб Master Data Services»
  Используйте диалоговое окно **Подключение к базе данных служб Master Data Services** для выбора базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]это диалоговое окно доступно на следующих страницах:  
  
-   На странице **Конфигурация базы данных** нажмите **Выбор базы данных** . Используйте это диалоговое окно для выбора базы данных, у которой надо настроить системные параметры.  
  
-   На странице **Веб-кофигурация** в **Связать веб-приложение с базой данных**щелкните **Выбрать** , чтобы выбрать базу данных для связи с веб-сайтом [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] или приложением.  
  
## <a name="select-database"></a>Выбор базы данных  
 Укажите информацию для соединения с локальным или удаленным экземпляром [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , на котором размещена база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Для подключения к удаленному экземпляру должны быть разрешены удаленные соединения.  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Экземпляр SQL Server**|Задайте имя экземпляра [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , на котором будет размещаться база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Можно использовать экземпляр по умолчанию или именованный экземпляр на локальном или удаленном компьютере. Укажите сведения, введя следующее:<br /><br /> Точка (.) для подключения к экземпляру по умолчанию на локальном компьютере.<br /><br /> Имя или IP-адрес сервера, чтобы подключиться к экземпляру по умолчанию на указанном локальном или удаленном компьютере.<br /><br /> Имя или IP-адрес сервера и имя экземпляра, чтобы подключиться к именованному экземпляру на указанном локальном или удаленном компьютере. Укажите эту информацию в формате *имя_сервера*\\*имя_экземпляра*.|  
|**Тип проверки подлинности**|Выберите тип проверки подлинности, который будет использоваться для соединения с указанным экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Учетные данные, используемые для соединения, определяют базы данных, отображающиеся в раскрывающемся списке **База данных служб Master Data Services** .<br /><br /> Имеются следующие типы проверки подлинности.<br /><br /> **Текущий пользователь — встроенная безопасность**. Для подключения используется встроенная проверка подлинности Windows (используются учетные данные учетной записи текущего пользователя Windows). [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] использует учетные данные Windows для пользователя, который вошел в систему и открыл приложение. Другие учетные данные Windows указать в приложении нельзя. Если необходимо подключиться с другими учетными данными, то следует войти в систему как пользователь с такими учетными данными, а затем открыть [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Учетная запись SQL Server**. Для подключения используется учетная запись SQL Server. При выборе этого параметра поля **Имя пользователя** и **Пароль** доступны для ввода и необходимо указать учетные данные учетной записи [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для заданного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**User name**|Укажите имя пользовательской учетной записи, которая будет использоваться для подключения к заданному экземпляру SQL-сервера. Учетная запись должна входить в роль **sysadmin** для указанного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :<br /><br /> Если **Тип проверки подлинности** — это **Текущий пользователь — встроенная безопасность**, поле **Имя пользователя** доступно только для чтения и содержит имя учетной записи пользователя Windows, который вошел в систему.<br /><br /> Если **Тип проверки подлинности** — это **Учетная запись SQL Server**, поле **Имя пользователя** доступно для ввода и в нем необходимо указать учетные данные учетной записи [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для заданного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**Пароль**|Укажите пароль для этой учетной записи пользователя:<br /><br /> Если **Тип проверки подлинности** — это **Текущий пользователь — встроенная безопасность**, поле **Пароль** доступно только для чтения, и для подключения используются учетные данные из учетной записи указанного пользователя Windows.<br /><br /> Если **Тип проверки подлинности** — это **Учетная запись SQL Server**, поле **Пароль** доступно для ввода и в нем необходимо указать пароль, связанный с указанной учетной записью пользователя.|  
|**Подключить**|Подключение к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с указанными учетными данными.|  
|**База данных служб Master Data Services**|Отображает базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в указанном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на основании следующих критериев.<br /><br /> Если пользователь входит в роль сервера **sysadmin** для этого экземпляра, отображаются все базы данных этого экземпляра [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> Если пользователь входит в роль **db_owner** каких-либо баз данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] этого экземпляра, отображаются эти базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br/> Дополнительные сведения о ролях SQL Server см. в разделах [Роли уровня сервера](../relational-databases/security/authentication-access/server-level-roles.md) и [Роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>См. также:  
 [Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   

[Установка и настройка служб Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)
  
  
