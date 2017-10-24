---
title: "Включить или отключить управление пакет R для SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 88337da76b3a44b9dc797fd1d9f187bfda7396c8
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>Включить или отключить управление пакет R для SQL Server

В этой статье описан процесс включения и отключения в новый компонент пакета управления 2017 г. SQL Server. Эта возможность позволяет администратору базы данных для управления установкой пакета на экземпляре. Функция использует новые роли базы данных предоставить пользователям возможность установки R-пакеты, которые им необходимы, или предоставить другим пользователям пакетов.

По умолчанию компонент внешнего пакета управления для SQL Server не работает, даже если были установлены обучения функции компьютера.

Чтобы [включить](#bkmk_enable) этот компонент состоит из двух этапов и требует помощь от администратора базы данных:

1.  Включение управления пакетами в экземпляре SQL Server (один раз для каждого экземпляра SQL Server).

2.  Включение управления пакетами в базе данных SQL Server (один раз для каждой базы данных SQL Server).

Чтобы [отключить](#bkmk_disable) компонент пакета управления отменить процесса удаления пакетов уровня базы данных и разрешения, а затем удаления ролей с сервера:

1.  Отключение управления пакетами для каждой базы данных (один раз для базы данных).

2.  Отключение управления пакетами в экземпляре SQL Server (один раз для каждого экземпляра).

## <a name="bkmk_enable"></a>Включение пакета управления

Чтобы включить или отключить управление пакетами требует служебную программу командной строки **RegisterRExt.exe**, входящий в состав **RevoScaleR** пакета.

1. Откройте командную строку и перейдите в папку, содержащую программу RegisterRExt.exe. Расположение по умолчанию — `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Выполните следующую команду, указав соответствующий аргументы для вашей среды:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает объекты уровня экземпляра на сервере SQL Server, которые необходимы для управления пакетами. Он также перезапускается панели запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию.

    Если пользователь не задан, используется текущий контекст безопасности.

2.  Чтобы добавить пакет управления на уровне базы данных, выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, используемые для управления разрешениями пользователя: `rpkgs-users`, `rpkgs-private`, и `rpkgs-shared`.

    Если пользователь не задан, используется текущий контекст безопасности.

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

4.  После включения функции можно использовать любой пользователь с соответствующими разрешениями [создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкции T-SQL для добавления пакетов. Пример того, как это работает см. в разделе [Установка дополнительных пакетов в SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="bkmk_disable"></a>Отключить управление пакетами

1.  Из командной строки с повышенными привилегиями выполните следующую команду, чтобы отключить управление пакетами на уровне базы данных:

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Выполните следующую команду один раз для каждой базы данных, в которых была использована пакета управления. Эта команда приведет к удалению объектов базы данных, связанные с управлением пакет из указанной базы данных. Также будут удалены все пакеты, которые были установлены с расположением защищенных файловой системы на компьютере с SQL Server.

2.  (Необязательно) После очистки всех баз данных на предыдущем шаге пакетов выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет компонент пакета управления из экземпляра.

## <a name="see-also"></a>См. также:

[Управление пакетами R для SQL Server](r-package-management-for-sql-server-r-services.md)

