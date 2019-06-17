---
title: Включение и отключение удаленного управления пакетами R - служб машинного обучения SQL Server
description: Включение удаленного управления пакетами R на SQL Server 2016 R Services или служб SQL Server 2017 машинного обучения (в базе данных)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4ce25830c3899ca0973fafe30c86489bfcdc949a
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140500"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Включение и отключение удаленного пакета управления для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается включение удаленного управления пакетов R на клиентской рабочей станции или другой сервер машинного обучения. После включения функции управления пакетами на сервере SQL Server, можно использовать команды RevoScaleR на клиентском компьютере для установки пакетов на SQL Server.

> [!NOTE]
> В настоящее время поддерживается управления библиотеками R; Поддержка Python уже запланирована.

Компонент внешнего пакета управления для SQL Server функция отключена по умолчанию. Необходимо запустить отдельный сценарий для включения функции, как описано в следующем разделе.

## <a name="overview-of-process-and-tools"></a>Общие сведения о процессе и средствах

Чтобы включить или отключить управление пакетами на сервере SQL Server, используйте служебную программу командной строки **RegisterRExt.exe**, входящий в состав **RevoScaleR** пакета.

[Включение](#bkmk_enable) эта функция представляет собой двухэтапный процесс, требуя администратором базы данных: Включение управления пакетами в экземпляре SQL Server (один раз для каждого экземпляра SQL Server), а затем Включение управления пакетами в базе данных SQL (один раз в SQL Server База данных).

[Отключение](#bkmk_disable) функцию управления пакетами также потребует выполнения multipel действий: удалите пакетов на уровне базы данных и разрешения (один раз в базе данных) и затем удалить роли с сервера (один раз для каждого экземпляра).

## <a name="bkmk_enable"></a> Включение управления пакетами

1. В SQL Server откройте командную строку с повышенными правами и перейдите к папке, содержащей программы, RegisterRExt.exe. Расположение по умолчанию — `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Выполните следующую команду, указав соответствующие аргументами для вашей среды:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает объекты уровня экземпляра на компьютере с SQL Server, которые необходимы для управления пакетами. Он также перезапускается панели запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию. Если пользователь не указан, используется текущий контекст безопасности. Например следующая команда включает управление пакетами в экземпляре в пути RegisterRExt.exe, используя учетные данные пользователя, открывшего командной строки:

    `REgisterRExt.exe /install pkgmgmt`

3. Чтобы добавить пакет управления для конкретной базы данных, выполните следующую команду из командной строки с повышенными правами:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, которые используются для управления разрешениями пользователей: `rpkgs-users`, `rpkgs-private`, и `rpkgs-shared`.

    Например следующая команда включает управление пакетами в базе данных на экземпляре, где запущена RegisterRExt. Если пользователь не указан, используется текущий контекст безопасности.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Выполните команду для каждой базы данных, где требуется установить пакеты.

5. Чтобы убедиться, что новые роли были успешно созданы, в SQL Server Management Studio, щелкните базу данных, разверните узел **безопасности**и разверните **ролей базы данных**.

    Можно также выполнить запрос на sys.database_principals, например следующие:

    ```sql
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

После включения этой функции, можно использовать функции RevoScaleR для установки или удаления пакетов из удаленного клиента R.

## <a name="bkmk_disable"></a> Отключение управления пакетами

1. Из командной строки с повышенными снова запустите программу RegisterRExt и отключение управления пакетами на уровне базы данных:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет объекты базы данных, связанные с управлением пакетами из указанной базы данных. Он также удаляет все пакеты, которые были установлены из защищенного расположения файловой системы на компьютере SQL Server.

2. Повторите эту команду в каждой базе данных, где использовалось управление пакетами.

3.  (Необязательно) После всех баз данных из пакетов с помощью на предыдущем шаге, выполните следующую команду из командной строки с повышенными правами:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет функцию управления пакетами из экземпляра. Может потребоваться вручную перезапустить службу панели запуска еще раз, чтобы увидеть изменения.

## <a name="next-steps"></a>Следующие шаги

+ [Использовать RevoScaleR для установки новых пакетов R](use-revoscaler-to-manage-r-packages.md)
+ [Советы по установке пакетов R](packages-installed-in-user-libraries.md)
+ [Пакеты по умолчанию](../package-management/default-packages.md)
