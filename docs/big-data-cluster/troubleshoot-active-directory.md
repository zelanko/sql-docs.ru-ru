---
title: Устранение неполадок при развертывании в режиме Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Устранение неполадок при развертывании кластера больших данных SQL Server в домене Active Directory.
author: rl-msft
ms.author: rafidl
ms.reviewer: mikeray
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d887eadd021641241516a1478c6ac13e0d0bdec
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79191215"
---
# <a name="troubleshoot-sql-server-big-data-cluster-active-directory-mode-deployment"></a>Устранение неполадок при развертывании кластера больших данных SQL Server в режиме Active Directory

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается устранение неполадок при развертывании кластера больших данных SQL Server в режиме Active Directory.

## <a name="check-deployment-progress"></a>Проверка хода выполнения развертывания

Развертывание может занять несколько минут. Если кластер не готов через 15 минут, обратитесь к журналам контроллера для получения дополнительных сведений.

При развертывании кластера проверьте объекты pod.

```console
kubectl get pods -n mssql-cluster
```

Убедитесь, что возвращаемый список объектов pod включает следующее:

- `compute-`$
- `data-`
- `storage-`

Если объекты pod compute, data и storage не создаются, обратитесь к журналам, чтобы определить причину.

## <a name="check-logs"></a>Проверка журналов

Чтобы определить, почему развертывание завершается без создания объектов pod compute, data и storage, обратитесь к следующим журналам: 

- Обратитесь к журналу `controller.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\control-<suffix>\controller\controller\<date>\controller.log`). Найдите следующую запись:

  `WARN | StatefulSet master is not ready with 0 ready pods and 3 unready pods `

- Обратитесь к журналу `master-0` `provisioner.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\master-0\mssql-server\provisioner\provisioner.log`)

  ```
  ERROR | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
    Traceback (most recent call last):
      File "/opt/provisioner/bin/scripts/provisioningpool.py", line 214, in executeNonQueries
        connection.execute_non_query(command)
      File "src/_mssql.pyx", line 1033, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1061, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1634, in _mssql.check_and_raise
      File "src/_mssql.pyx", line 1683, in _mssql.maybe_raise_MSSQLDatabaseException
    _mssql.MSSQLDatabaseException: (15401, b"Windows NT user or group '<domain>.<top-level-domain>\\<domain-group>' not found. Check the name again.DB-Lib error message 20018, severity 16:\nGeneral SQL Server error: Check messages from the SQL Server\n")
  WARNING | [3/3] Provisioning exception occurred during provisioning step: ProvisioningMasterPool.
  WARNING | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
  WARNING | Retrying.
  ```

  В примере выше развертыванию не удается создать имя входа для пользователя домена, поскольку доменная группа ограничена локальным доменом. Используйте группы домена с глобальной или универсальной областью. Требования к области группы AD указаны в разделе [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](deploy-active-directory.md).

## <a name="check-the-scope-of-domain-groups"></a>Проверьте область групп домена.

Проверьте область группы домена (<`domain-group`>). Используйте [get-adgroup](/powershell/module/addsadministration/get-adgroup/).

Если областью группы `<domain-group>` является локальный домен (`DomainLocal`), развертывание завершается сбоем. 

Следующий сценарий PowerShell проверяет область двух групп AD с именами `bdcadmins` и `bdcusers`. Замените имена на имена своих групп. 

```powershell
#Administrators and users AD groups
$Cluster_admins_group='bdcadmins'
$Cluster_users_group='bdcusers'

#Performing AD Group Checks...

#AD admin group Check
$ClusterAdminGroupScope_Result = New-Object System.Collections.ArrayList
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_admins_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterAdminGroupScope_Result.Add("Misconfiguration - $Cluster_admins_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal") 
    }
    else {
        [void]$ClusterAdminGroupScope_Result.Add("OK - $Cluster_admins_group Group scope is $GroupScope")
    }
}
catch {
    [void]$ClusterAdminGroupScope_Result.Add("Error - " + $_.exception.message)
}
#Ad users group check
$ClusterUsersGroupScope_Result = New-Object System.Collections.ArrayList
$GroupScope = ''
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_users_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterUsersGroupScope_Result.Add("Misconfiguration - $Cluster_users_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal")
    } 
    else 
    { [void]$ClusterUsersGroupScope_Result.Add("OK - $Cluster_users_group Group scope is $GroupScope") }
}
catch {
    [void]$ClusterUsersGroupScope_Result.Add("Error - " + $_.exception.message)
}

#Display the results
$ClusterUsersGroupScope_Result
```

## <a name="check-security-support-container"></a>Проверка контейнера security-support 

Ознакомьтесь с журналами контейнера security-support.

Следующая команда собирает журналы security-support в кластере в пространстве имен `mssql-cluster`.

```console
azdata bdc debug copy-logs -n mssql-cluster -c security-support
```

Извлеките журналы и найдите `\mssql-cluster\control-<identifier>\controller\control-rts5t-controller-stdout.log`.

Найдите в журнале следующие записи:

```
ERROR    | Failed to create AD user account 'cntrl-controller'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=cntrl-controller,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'ldap-user'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=ldap-user,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'nginx-mgmtproxy'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=nginx-mgmtproxy,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform.
```

Эти записи могут появиться, когда у DNS-сервера контроллера домена отсутствует обратная запись DNS (запись типа PTR).

## <a name="verify-reverse-lookup-ptr-record"></a>Проверка обратного просмотра (записи типа PTR)
    
Выполните следующий сценарий PowerShell, чтобы убедиться, что обратная запись DNS (запись типа PTR) настроена.

```powershell
#Domain Controller FQDN 'DCserver01.contoso.local'
$Domain_controller_FQDN = 'DCserver01.contoso.local'

#Performing Domain Controller DNS record, reverse PTR Checks...
$DcControllerDnsPtr_Result = New-Object System.Collections.ArrayList
try {
    $Domain_controller_DNS_Record = Resolve-DnsName $Domain_controller_FQDN -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop
    foreach ($ip in $Domain_controller_DNS_Record.IPAddress) {
        #resolving hostname by IP address to make sure we have reverse PTR record 
        if ((Resolve-DnsName $ip).NameHost -eq $Domain_controller_FQDN) {
            [void]$DcControllerDnsPtr_Result.add("OK - $Domain_controller_FQDN has an A record with an IP $ip, Reverse PTR record is in place") 
        }
        else {
            [void]$DcControllerDnsPtr_Result.add("Missing - $Domain_controller_FQDN has an A record with an IP $ip, But no reverse PTR record was found for the host")
        }
    }
}
catch {
    [void]$DcControllerDnsPtr_Result.add("Error - " + $_.exception.message)
}

#show the results 
$DcControllerDnsPtr_Result
```

[Проверьте обратную запись DNS (запись типа PTR) для контроллера домена](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller).