---
title: Использование идентификаторов безопасности для предоставления разрешений службам в SQL Server | Документация Майкрософт
author: randomnote1
ms.author: dareist
ms.date: 05/02/2019
ms.topic: conceptual
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.openlocfilehash: 1a0bd129fc535b53d8d19ad76f99f3a86ba10c11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65135240"
---
# <a name="using-service-sids-to-grant-permissions-to-services-in-sql-server"></a>Использование идентификаторов безопасности для предоставления разрешений службам в SQL Server

SQL Server использует [идентификаторы безопасности (SID) отдельных служб](https://support.microsoft.com/help/2620201/sql-server-uses-a-service-sid-to-provide-service-isolation) для предоставления разрешения на доступ непосредственно к конкретной службе. Этот метод используется в SQL Server для предоставления разрешений в службах ядра и агента (NT SERVICE\MSSQL$<InstanceName> и NT SERVICE\SQLAGENT$<InstanceName> соответственно). При использовании этого метода ядро базы данных будет доступно этим службам только в том случае, если они работают.

Этот же метод можно использовать при предоставлении разрешений для других служб. Использование идентификатора безопасности службы устраняет затраты на управление и обслуживание учетных записей служб и обеспечивает более жесткий, детальный контроль над разрешениями, предоставленными для системных ресурсов.

Ниже приведены примеры служб, где можно использовать идентификатор безопасности службы.

- Служба работоспособности System Center Operations Manager (NT SERVICE\HealthService)
- Служба кластера WSFC (NT SERVICE\ClusSvc)

По умолчанию некоторые службы не имеют идентификатора безопасности службы. Идентификатор безопасности службы должен быть создан с помощью программы [SC.exe](https://docs.microsoft.com/windows/desktop/services/configuring-a-service-using-sc). [Этот метод](https://kevinholman.com/2016/08/25/sql-mp-run-as-accounts-no-longer-required/) была принят администраторами Microsoft System Center Operations Manager для предоставления разрешений службе работоспособности в SQL Server.

Когда идентификатор безопасности создан и подтвержден, ему должно быть предоставлено разрешение в SQL Server. Предоставление разрешений достигается путем создания имени входа Windows с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или запроса. После создания имени входа ему можно предоставить разрешения, добавлять в роли и сопоставлять с базами данных так же, как и любое другое имя входа.

> [!TIP]
> Если происходит ошибка `Login failed for user 'NT AUTHORITY\SYSTEM'`, убедитесь, существует ли идентификатор безопасности службы для данной службы, было ли имя входа безопасности службы создано в SQL Server и были ли для идентификатора безопасности службы в SQL Server предоставлены соответствующие разрешения.

## <a name="security"></a>безопасность

### <a name="eliminate-service-accounts"></a>Устранение учетных записей служб

Традиционно учетные записи служб использовались для входа в SQL Server. Учетные записи служб добавляют дополнительный уровень сложности управления из-за необходимости использовать и периодически обновлять пароль учетной записи службы. Кроме того, учетные данные учетной записи службы могут использоваться при попытке маскировать действия пользователя в экземпляре.

### <a name="granular-permissions-to-system-accounts"></a>Детализированные разрешения для системных учетных записей

Системные учетные записи традиционно получали разрешения путем создания имени входа для учетных записи [LocalSystem](https://msdn.microsoft.com/library/windows/desktop/ms684190) ([NT AUTHORITY\SYSTEM в en-us](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions#Localized_service_names)) или [NetworkService](https://docs.microsoft.com/windows/desktop/Services/networkservice-account) ([NT AUTHORITY\NETWORK SERVICE в en-us](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions?#Localized_service_names)) и предоставления им разрешений. Этот метод предоставляет любому процессу или службе, которые выполняются как системная учетная запись, разрешения в SQL.

С помощью идентификатора безопасности службы разрешения могут быть предоставлены для конкретной службы. Только эта служба имеет доступ к ресурсам, для которых ей были предоставлены разрешения, действующие во время ее выполнения. Например, если `HealthService` выполняется как `LocalSystem` и получает право `View Server State`, `LocalSystem` учетная запись будет иметь право на `View Server State` только при выполнении в контексте `HealthService`. Если другой процесс попытается получить доступ к состоянию сервера SQL как `LocalSystem`, ему будет отказано в доступе.

## <a name="examples"></a>Примеры

### <a name="a-create-a-service-sid"></a>A. Создание идентификатора безопасности

Следующая команда PowerShell создает идентификатор безопасности службы для службы работоспособности System Center Operations Manager.

```PowerShell
sc.exe --% sidtype "HealthService" unrestricted
```

> [!IMPORTANT]
> `--%` приказывает PowerShell остановить анализ остальной части команды. Это полезно при использовании устаревших команд и приложений.

### <a name="b-query-a-service-sid"></a>Б. Запрос идентификатора безопасности службы

Для проверки самого идентификатора безопасности службы или факта его наличия выполните следующую команду в PowerShell.

```PowerShell
sc.exe --% qsidtype "HealthService"
```

> [!IMPORTANT]
> `--%` приказывает PowerShell остановить анализ остальной части команды. Это полезно при использовании устаревших команд и приложений.

### <a name="c-add-a-newly-created-service-sid-as-a-login"></a>В. Добавление только что созданного идентификатора безопасности службы в качестве имени входа

В следующем примере создается имя входа для службы работоспособности System Center Operations Manager с помощью T-SQL.

```SQL
CREATE LOGIN [NT SERVICE\HealthService] FROM WINDOWS
GO
```

### <a name="d-add-an-existing-service-sid-as-a-login"></a>Г. Добавление существующего идентификатора безопасности службы в качестве имени входа

В следующем примере создается имя входа для службы кластеров с помощью T-SQL. Предоставление разрешений службе кластеров напрямую избавляет от необходимости предоставлять избыточные разрешения системной учетной записи.

```SQL
CREATE LOGIN [NT SERVICE\ClusSvc] FROM WINDOWS
GO
```

### <a name="e-grant-permissions-to-a-service-sid"></a>Д. Предоставление разрешений идентификатору безопасности

Предоставление разрешения, необходимого для настройки групп доступности в службе кластеров.

```SQL
GRANT ALTER ANY AVAILABILITY GROUP TO 'NT SERVICE\ClusSvc'
GO

GRANT CONNECT SQL TO 'NT SERVICE\ClusSvc'
GO

GRANT VIEW SERVER STATE TO 'NT SERVICE\ClusSvc'
GO
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о структуре идентификаторов безопасности см. в разделе [Структура SERVICE_SID_INFO](https://docs.microsoft.com/windows/desktop/api/winsvc/ns-winsvc-_service_sid_info).

Сведения о дополнительных доступных параметрах см. в разделе [Создание имени входа](https://docs.microsoft.com/sql/t-sql/statements/create-login-transact-sql).

Чтобы использовать безопасность на основе ролей с идентификаторами безопасности службы, ознакомьтесь с разделом [Создание ролей](https://docs.microsoft.com/sql/t-sql/statements/create-role-transact-sql) в SQL Server.

Изучите различные способы [предоставления разрешений](https://docs.microsoft.com/sql/t-sql/statements/grant-transact-sql) идентификаторам безопасности службы в SQL Server.
