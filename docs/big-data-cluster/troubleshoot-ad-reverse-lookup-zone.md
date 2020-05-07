---
title: Развертывание в режиме с AD остановлено — нет записи зоны обратного поиска для контроллера домена
titleSuffix: SQL Server Big Data Cluster
description: При развертывании BDC в режиме с AD система перестает отвечать она запросы из-за отсутствующей записи зоны обратного поиска для контроллера домена на DNS-сервере контроллера домена.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 04/21/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4cac5fe891533d623a686a02641f63cb25d4b17f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "82154159"
---
# <a name="ad-mode-deployment-stopped---missing-reverse-lookup-zone-entry-for-dc"></a>Развертывание в режиме с AD остановлено — нет записи зоны обратного поиска для контроллера домена

При развертывании BDC в режиме с Active Directory (AD) система перестает отвечать она запросы. Проверьте симптомы, чтобы определить, является ли причиной отсутствие записи зоны обратного поиска на DNS-сервере контроллера домена. 

## <a name="symptom"></a>Симптом

Вы начали развертывать кластер больших данных (BDC) в режиме с AD, но развертывание зависает и не выполняется.

В примере ниже показаны результаты развертывания в оболочке bash.

```
The privacy statement can be viewed at:
https://go.microsoft.com/fwlink/?LinkId=853010
 
The license terms for SQL Server Big Data Cluster can be viewed at:
Enterprise: https://go.microsoft.com/fwlink/?linkid=2104292
Standard: https://go.microsoft.com/fwlink/?linkid=2104294
Developer: https://go.microsoft.com/fwlink/?linkid=2104079
 
Cluster deployment documentation can be viewed at:
https://aka.ms/bdc-deploy
 
NOTE: Cluster creation can take a significant amount of time depending on
configuration, network speed, and the number of nodes in the cluster.
 
Starting cluster deployment.
Cluster controller endpoint is available at bdc-control.contoso.com:30080, 193.168.5.14:30080.
Waiting for control plane to be ready after 5 minutes.
Waiting for control plane to be ready after 10 minutes.
Waiting for control plane to be ready after 15 minutes.
Waiting for control plane to be ready after 20 minutes.
Waiting for control plane to be ready after 25 minutes.
```

Проверьте имеющиеся развернутые объекты pod.

```bash
kubectl get pods -n mssql-cluster
```

Приведенные ниже результаты указывают, что развернуты только те объекты pod, которые принадлежат контроллеру. Объекты pod для вычислительных ресурсов, данных или хранилища не созданы.

```
NAME              READY   STATUS    RESTARTS   AGE
control-rts5t     3/3     Running   0          18m
controldb-0       2/2     Running   0          18m
controlwd-csgst   1/1     Running   0          16m
dns-7kfnz         2/2     Running   0          16m
logsdb-0          1/1     Running   0          16m
logsui-2pc29      1/1     Running   0          16m
metricsdb-0       1/1     Running   0          16m
metricsdc-4rtm4   1/1     Running   0          16m
metricsdc-6lr2t   1/1     Running   0          16m
metricsdc-ftx9m   1/1     Running   0          16m
metricsdc-h59jb   1/1     Running   0          16m
metricsui-lvdpt   1/1     Running   0          16m
mgmtproxy-mkmxp   2/2     Running   0          16m
```

Изучите данные в журналах контейнера security-support. Проверьте, есть ли ошибки LDAP. 

## <a name="check-security-support-container"></a>Проверка контейнера security-support 

Ознакомьтесь с журналами контейнера security-support.

Следующая команда собирает журналы security-support в кластере в пространстве имен `mssql-cluster`.

```bash
azdata bdc debug copy-logs -n mssql-cluster -c security-support
```

Извлеките журналы и найдите `\mssql-cluster\control-<identifier>\controller\control-rts5t-controller-stdout.log`.

> [!TIP]
> Собрать журналы можно несколькими способами. Вы можете не копировать журналы с помощью команды `azdata`, а просто воспользоваться записной книжкой в Azure Data Studio.
> В Azure Data Studio подключитесь к кластеру Kubernetes и запустите соответствующую записную книжку для устранения неполадок. Вот примеры записных книжек:
>
> - TSG027 — наблюдение за развертыванием кластера
> - TSG061 — получение заключительного фрагмента журналов контейнеров для модулей pod в пространстве имен кластера больших данных
> - TSG001 — выполнение команды `azdata` copy-logs.
>

## <a name="inspect-the-logs"></a>Изучение журналов

Найдите журнал. Следующий пример указывает на журнал развертывания контроллера. 

`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-YYYYMMDD-HHMMSS\<namespace>\control-<identifier>\controller\control-<identifier>-controller-stdout.log`"

```
YYYY-MM-DD HH:MM:SS.ms | ERROR | Failed to create AD user account 'cntrl-controller'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=cntrl-controller,OU=bdc, DC=CONTOSO, DC=com' to 'CONTOSO.COM': Server is unwilling to perform. 
YYYY-MM-DD HH:MM:SS.ms | ERROR | Failed to create AD user account 'ldap-user'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=ldap-user,OU=bdc, DC=CONTOSO, DC=com' to 'CONTOSO.COM': Server is unwilling to perform. 
YYYY-MM-DD HH:MM:SS.ms | ERROR | Failed to create AD user account 'nginx-mgmtproxy'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=nginx-mgmtproxy,OU=bdc, DC=CONTOSO, DC=com' to 'CONTOSO.COM': Server is unwilling to perform. 
```

## <a name="cause"></a>Причина

Нет записи зоны обратного поиска для контроллера домена в записи DNS контроллера домена. 

## <a name="resolution"></a>Решение

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

## <a name="next-steps"></a>Дальнейшие действия

[Проверьте обратную запись DNS (запись типа PTR) для контроллера домена](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller).
