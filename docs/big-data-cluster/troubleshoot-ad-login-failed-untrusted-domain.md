---
title: Сбой входа в режим AD — недоверенный домен
titleSuffix: SQL Server Big Data Cluster
description: 'Исправление поведения: клиенты не проходят проверку подлинности при настройке DNS-записей конечных точек в качестве CNAME, указывающих на имя псевдонима.'
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 05/01/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2cc173ca162ea69e65bce477f83e5ff6f75ac69a
ms.sourcegitcommit: f6200d3d9cdf2627b243384835dc37d2bd40480e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82785273"
---
# <a name="symptom-ad-mode-login-fails---untrusted-domain-big-data-clusters"></a>Симптом. Сбой входа в режим AD — недоверенный домен (кластеры больших данных)

В кластере больших данных (BDC) SQL Server в режиме Active Directory попытки подключения могут завершиться сбоем и возвращают следующую ошибку:

`Login failed. The login is from an untrusted domain and cannot be used with Integrated authentication.`

Это может произойти, если вы настроили записи DNS как CNAME, указывающие на псевдоним обратного прокси-сервера, который распределяет трафик по узлам Kubernetes.

## <a name="root-cause"></a>Первопричина

Когда конечные точки настроены с записями DNS с CNAME, указывающими на псевдоним обратного прокси-сервера, который распределяет трафик по узлам Kubernetes:

- Процесс проверки подлинности Kerberos выполняет поиск имени субъекта-службы (SPN), соответствующего записи CNAME, а не настоящее имя субъекта-службы, зарегистрированное BDC в Active Directory
- Сбой проверки подлинности 

## <a name="confirm-root-cause"></a>Подтверждение первопричины

После сбоя проверки подлинности проверьте кэш билетов Kerberos. 

Чтобы проверить кэш билетов, используйте команду `klist`. 

Найдите билет с именем субъекта-службы, соответствующим конечной точке, к которой вы пытались подключиться.

Ожидаемый билет отсутствует.

В этом примере главная конечная точка, запись DNS `bdc-sql`, представляет собой CNAME, настроенный на обратный прокси-сервер с именем `ServerReverseProxy`

```PowerShell
Resolve-DnsName bdc-sql
```

В следующем разделе показаны результаты предыдущей команды.

```
Name                           Type   TTL   Section    NameHost
----                           ----   ---   -------    --------
bdc-sql.mydomain.com           CNAME  3600  Answer     ReverseProxyServer.mydomain.com

Name       : ReverseProxyServer.mydomain.com
QueryType  : A
TTL        : 3600
Section    : Answer
IP4Address : 193.168.5.10
```

>[!NOTE]
>Следующий раздел ссылается на [`tshark`](https://www.wireshark.org/docs/man-pages/tshark.html). `tshark` — это служебная программа командной строки, установленная в составе служебной программы трассировки сети [Wireshark](https://www.wireshark.org/docs/)).

Чтобы просмотреть имя субъекта-службы, запрошенное из Active Directory, используйте `tshark`. Следующая команда ограничивает захват трассировки сети только протоколом Kerberos и отображает только сообщения `krb-error (30)`. Среди них должны быть сообщения о неудачных запросах имени участника-службы.

```bash
tshark -Y "kerberos && kerberos.msg_type == 30" -T fields -e kerberos.error_code -e kerberos.SNameString
```

В другой командной оболочке попробуйте подключиться к главному модулю pod:

```bash
klist purge

sqlcmd -S bdc-sql.mydomain.com,31433 -E
```

См. следующий пример выходных данных.

```bash
klist purge

Current LogonId is 0:0xf6b58
        Deleting all tickets:
        Ticket(s) purged!

sqlcmd -S bdc-sql.mydomain.com,31433 -E
sqlcmd: Error: Microsoft ODBC Driver 17 for SQL Server : Login failed. The login is from an untrusted domain and cannot be used with Integrated authentication.
```

Просмотрите выходные данные `tshark`. 

```bash
Capturing on 'Ethernet 3'
25      krbtgt,RLAZURE.COM
7       MSSQLSvc,ReverseProxyServer.mydomain.com:31433
2 packets captured
```

Обратите внимание, что клиент запрашивает `SPN MSSQLSvc,ReverseProxyServer.mydomain.com:31433`, который не существует. В итоге попытка подключения завершается ошибкой 7. Ошибка 7 означает `KRB5KDC_ERR_S_PRINCIPAL_UNKNOWN Server not found in Kerberos database`.

В правильной конфигурации клиент запрашивает имя субъекта-службы, зарегистрированное BDC. В этом примере правильным именем субъекта-службы было бы `MSSQLSvc,bdc-sql.mydomain.com:31433`.

>[!NOTE]
>Ошибка 25 означает `KDC_ERR_PREAUTH_REQUIRED` — требуется дополнительная предварительная проверка подлинности. Ее можно спокойно проигнорировать. `KDC_ERR_PREAUTH_REQUIRED` возвращается при первом запросе Kerberos AD. По умолчанию клиент Windows Kerberos не включает сведения о предварительной проверке подлинности в первом запросе.

Чтобы просмотреть список имен субъектов-служб, зарегистрированных BDC для главной конечной точки, выполните `setspn -L mssql-master`. 

См. следующий пример выходных данных:

```bash
Registered ServicePrincipalNames for CN=mssql-master,OU=bdc,DC=mydomain,DC=com:
        MSSQLSvc/bdc-sqlread.mydomain.com:31436
        MSSQLSvc/-sqlread:31436
        MSSQLSvc/bdc-sqlread.mydomain.com
        MSSQLSvc/bdc-sqlread
        MSSQLSvc/bdc-sql.mydomain.com:31433
        MSSQLSvc/bdc-sql:31433
        MSSQLSvc/bdc-sql.mydomain.com
        MSSQLSvc/bdc-sql
        MSSQLSvc/master-p-svc.mydomain.com:1533
        MSSQLSvc/master-p-svc:1533
        MSSQLSvc/master-p-svc.mydomain.com:1433
        MSSQLSvc/master-p-svc:1433
        MSSQLSvc/master-p-svc.mydomain.com
        MSSQLSvc/master-p-svc
        MSSQLSvc/master-svc.mydomain.com:1533
        MSSQLSvc/master-svc:1533
        MSSQLSvc/master-svc.mydomain.com:1433
        MSSQLSvc/master-svc:1433
        MSSQLSvc/master-svc.mydomain.com
        MSSQLSvc/master-svc
```

В результатах выше адрес обратного прокси-сервера не должен быть зарегистрирован.

## <a name="resolve"></a>Разрешить

В этом разделе показано два способа решения проблемы. После внесения соответствующих изменений запустите `ipconfig -flushdns` и `klist purge` в клиенте. Затем повторите попытку подключения.

### <a name="option-1"></a>Вариант 1

Удалите запись CNAME для каждой конечной точки BDC в DNS и замените ее на несколько записей `A`, указывающих на каждый узел Kubernetes или каждый главный узел Kubernetes, если у вас есть несколько главных узлов.

>[!TIP]
>Описанный ниже скрипт использует PowerShell. Дополнительные сведения см. в статье [Установка PowerShell на Linux](/powershell/scripting/install/installing-powershell-core-on-linux).

Вы можете использовать следующий скрипт PowerShell для обновления записей конечных точек DNS. Запустите скрипт с любого компьютера, подключенного к тому же домену:

```powershell
#Specify the DNS server, example contoso.local
$Domain_DNS_name=mydomain.com'

#DNS records for bdc endpoints
$Controller_DNS_name = 'bdc-control'
$Managment_proxy_DNS_name= 'bdc-proxy'
$Master_Primary_DNS_name = 'bdc-sql'
$Master_Secondary_DNS_name = 'bdc-sqlread'
$Gateway_DNS_name = 'bdc-gateway'
$AppProxy_DNS_name = 'bdc-appproxy'

#Performing Endpoint DNS records Checks..

#Build array of endpoints 
$BdcEndpointsDns = New-Object System.Collections.ArrayList

[void]$BdcEndpointsDns.Add($Controller_DNS_name)
[void]$BdcEndpointsDns.Add($Managment_proxy_DNS_name)
[void]$BdcEndpointsDns.Add($Master_Primary_DNS_name)
[void]$BdcEndpointsDns.Add($Master_Secondary_DNS_name)
[void]$BdcEndpointsDns.Add($Gateway_DNS_name)
[void]$BdcEndpointsDns.Add($AppProxy_DNS_name)

#Build arrary for results 
$BdcEndpointsDns_Result = New-Object System.Collections.ArrayList

foreach ($DnsName in $BdcEndpointsDns) {
    try {
        $endpoint_DNS_record = Resolve-DnsName $DnsName -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop 
        foreach ($ip in $endpoint_DNS_record.IPAddress) {
            [void]$BdcEndpointsDns_Result.Add("OK - $DnsName is an A record with an IP $ip")
        }
    }
    catch {
        [void]$BdcEndpointsDns_Result.Add("MisConfiguration - $DnsName is not an A record or does not exists")
    }  
}

#show the results 
$BdcEndpointsDns_Result
```

### <a name="option-2"></a>Вариант 2

Кроме того, можно обойти эту ошибку, изменив запись CNAME так, чтобы она указывала на IP-адрес обратного прокси-сервера, а не его имя.

## <a name="confirm-resolution"></a>Подтверждение разрешения

После внесения исправлений с использованием одного из указанных вариантов подтвердите исправление, подключившись к кластеру больших данных с помощью Active Directory.

## <a name="next-steps"></a>Дальнейшие действия

[Проверьте обратную запись DNS (запись типа PTR) для контроллера домена](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller).
