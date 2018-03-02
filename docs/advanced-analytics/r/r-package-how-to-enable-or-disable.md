---
title: "Включение и отключение удаленного пакета управления для SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: feb30d37f9c22d6620a7c6a734172ef43c15e253
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Включение и отключение удаленного пакета управления для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается включение управления пакетов R от удаленного экземпляра сервера Machine обучения. После включения функции управления пакета RevoScaleR команды используются для установки пакетов в базе данных с удаленного клиента.

> [!NOTE]
> В настоящее время поддерживается управления библиотеками R; Поддержка Python поддержку такой возможности.

По умолчанию компонент внешнего пакета управления для SQL Server не работает, даже если были установлены обучения функции компьютера. Необходимо запустить отдельный скрипт для включения функции, как описано в следующем разделе.

## <a name="overview-of-process-and-tools"></a>Общие сведения о процессе и средствах

Чтобы включить или отключить управление пакетами, используйте служебную программу командной строки **RegisterRExt.exe**, входящий в состав **RevoScaleR** пакета.

[Включение](#bkmk_enable) эта функция представляет собой двухэтапный процесс, требующие администратором базы данных: можно включить управление пакетами в экземпляре SQL Server (один раз в экземпляре SQL Server), а затем включите управление пакетами в базе данных SQL (один раз в SQL Server База данных).

[Отключение](#bkmk_disable) пакета управления также требуется действия multipel: можно удалить пакеты уровня базы данных и разрешения (один раз в базе данных), а затем удалите ролей с сервера (один раз в экземпляр).

## <a name="bkmk_enable"></a> Включение пакета управления

1. Откройте командную строку и перейдите в папку, содержащую программу RegisterRExt.exe. Расположение по умолчанию — `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Выполните следующую команду, указав соответствующих аргументов для вашей среды:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает объекты уровня экземпляра на сервере SQL Server, которые необходимы для управления пакетами. Он также перезапускается панели запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию. Если пользователь не задан, используется текущий контекст безопасности. Например следующая команда включает управление пакетами в экземпляре в пути RegisterRExt.exe, используя учетные данные пользователя, открывшего командной строки:

    `REgisterRExt.exe /installpkgmgmt`

3. Чтобы добавить пакет управления для конкретной базы данных, выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, используемые для управления разрешениями пользователя: `rpkgs-users`, `rpkgs-private`, и `rpkgs-shared`.

    Например следующая команда включает управление пакетами в базе данных на экземпляре, где запущена RegisterRExt. Если пользователь не задан, используется текущий контекст безопасности.

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

4. Выполните команду для каждой базы данных, где необходимо установить пакеты.

5. Чтобы убедиться, что новые роли были успешно созданы, в SQL Server Management Studio выберите базу данных, разверните узел **безопасности**и разверните **ролей базы данных**.

    Можно также выполнить запрос к sys.database_principals из следующего:

    ```SQL
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

После включения этой функции можно использовать функции RevoScaleR для установки или удаления пакетов из удаленного клиента R.

## <a name="bkmk_disable"></a> Отключить управление пакетами

1. Из командной строки с повышенными привилегиями запустите программу RegisterRExt еще раз и отключение пакета управления на уровне базы данных.

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет объекты базы данных, связанные с управлением пакет из указанной базы данных. Она также удаляет все пакеты, которые были установлены с расположением защищенных файловой системы на компьютере с SQL Server.

2. Повторите эту команду для каждой базы данных, где использовался пакета управления.

3.  (Необязательно) После очистки всех баз данных на предыдущем шаге пакетов выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет компонент пакета управления из экземпляра. Может потребоваться вручную перезапустить службу запуска еще раз, чтобы увидеть изменения.

