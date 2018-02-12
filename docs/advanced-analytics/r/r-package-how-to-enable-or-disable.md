---
title: "Включить или отключить управление пакет R для SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 01/04/2018
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
ms.openlocfilehash: 35bcae1e29e9b640d2e04b9adc788e382b18b6e8
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>Включить или отключить управление пакет R для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описаны новые возможности пакета управления в SQL Server 2017 г., позволяет администратору базы данных для управления установкой пакета на экземпляре, с помощью T-SQL, а не R.

Озже включена frature управления пакета, также команды R для установки пакетов на databae frm удаленного клиента.

> [!NOTE]
> По умолчанию компонент внешнего пакета управления для SQL Server не работает, даже если были установлены обучения функции компьютера. 

## <a name="enable-package-management"></a>Включение пакета управления

Чтобы [включить](#bkmk_enable) эта функция представляет собой двухэтапный процесс, требующие администратором базы данных:

1.  Включение управления пакетами в экземпляре SQL Server (один раз для каждого экземпляра SQL Server).

2.  Включение управления пакетами в базе данных SQL Server (один раз для каждой базы данных SQL Server).

Чтобы [отключить](#bkmk_disable) компонент пакета управления отменить процесса удаления пакетов уровня базы данных и разрешения, а затем удаления ролей с сервера:

1.  Отключение управления пакетами для каждой базы данных (один раз для базы данных).

2.  Отключение управления пакетами в экземпляре SQL Server (один раз для каждого экземпляра).

## <a name="bkmk_enable"></a>Включение пакета управления

Чтобы включить или отключить управление пакетами, используйте служебную программу командной строки **RegisterRExt.exe**, входящий в состав **RevoScaleR** пакета.

1. Откройте командную строку и перейдите в папку, содержащую программу RegisterRExt.exe. Расположение по умолчанию — `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Выполните следующую команду, указав соответствующих аргументов для вашей среды:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает объекты уровня экземпляра на сервере SQL Server, которые необходимы для управления пакетами. Он также перезапускается панели запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию. Если пользователь не задан, используется текущий контекст безопасности. Например следующая команда включает управление пакетами в экземпляре в пути RegisterRExt.exe, используя учетные данные пользователя, открывшего командной строки:

    `REgisterRExt.exe /installpkgmgmt`

2.  Чтобы добавить пакет управления для конкретной базы данных, выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, используемые для управления разрешениями пользователя: `rpkgs-users`, `rpkgs-private`, и `rpkgs-shared`.

    Например следующая команда включает управление пакетами в базе данных на экземпляре, где запущена RegisterRExt. Если пользователь не задан, используется текущий контекст безопасности. 

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

3. Выполните команду для каждой базы данных, где необходимо установить пакеты.

4.  Чтобы убедиться, что новые роли были успешно созданы, в SQL Server Management Studio выберите базу данных, разверните узел **безопасности**и разверните **ролей базы данных**.

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

4.  После включения функции можно подключиться к серверу и установить или синхронизировать пакеты удаленно, с помощью команды R. Пример того, как это работает см. в разделе [Установка дополнительных пакетов в SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="bkmk_disable"></a>Отключить управление пакетами

1.  Из командной строки с повышенными привилегиями запустите программу RegisterRExt еще раз и отключение пакета управления на уровне базы данных.

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет объекты базы данных, связанные с управлением пакет из указанной базы данных. Она также удаляет все пакеты, которые были установлены с расположением защищенных файловой системы на компьютере с SQL Server.

2. Выполните следующую команду один раз для каждой базы данных, в которых была использована пакета управления. 

3.  (Необязательно) После очистки всех баз данных на предыдущем шаге пакетов выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет компонент пакета управления из экземпляра. Может потребоваться вручную перезапустить службу запуска еще раз, чтобы увидеть изменения.

## <a name="see-also"></a>См. также:

[Управление пакетами R для SQL Server](r-package-management-for-sql-server-r-services.md)
