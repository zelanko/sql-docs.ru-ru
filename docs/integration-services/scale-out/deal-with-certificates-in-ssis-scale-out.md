---
title: "Работа с сертификатами в SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e09fec1fcf9cf0221dad50d708adef773b297237
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Работа с сертификатами в SQL Server Integration Services (SSIS) Scale Out

В Scale Out для защиты связи между мастером Scale Out и рабочей ролью Scale Out применяются два сертификата — для мастера и для рабочей роли. 

## <a name="scale-out-master-certificate"></a>Сертификат мастера Scale Out

В большинстве случаев сертификат мастера Scale Out настраивается во время установки мастера Scale Out.

На странице **Настройка Integration Services Scale Out — главный узел** мастера установки SQL Server вы можете создать самозаверяющий SSL-сертификат или воспользоваться существующим.

![Конфигурация мастера](media/master-config.PNG)

Если у вас нет особых требований к сертификатам, можете создать самозаверяющий SSL-сертификат. Для него можно дополнительно указать общие имена. Не забудьте включить в их число имя узла конечной точки мастера, которую потом будет использовать рабочая роль Scale Out. По умолчанию включаются имя компьютера и IP-адрес узла мастера. 

Если вы решили использовать существующий сертификат, нажмите кнопку "Обзор...", чтобы выбрать SSL-сертификат из **корневого** хранилища сертификатов на локальном компьютере.

### <a name="change-scale-out-master-certificate"></a>Изменение сертификата мастера Scale Out

Вам может потребоваться сменить сертификат мастера Scale Out из-за истечения срока действия сертификата или по другим причинам. Выполните следующие действия:

#### <a name="1-create-a-ssl-certificate"></a>1. Создание SSL-сертификата
Создайте и установите SSL-сертификат на узле мастера с помощью следующей команды:
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Пример
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Привязка сертификата к порту мастера
Проверьте исходные привязки с помощью команды:
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Пример
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Удалите исходные привязки и настройте новую с помощью следующих команд:
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Пример
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Обновление файла конфигурации для службы мастера Scale Out
Обновите файл конфигурации для службы мастера Scale Out (\<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config) на узле мастера. Обновите **SSLCertThumbprint**, используя отпечаток нового SSL-сертификата.

#### <a name="4-restart-scale-out-master-service"></a>4. Перезапуск службы мастера Scale Out

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Повторное подключение рабочей роли Scale Out к мастеру Scale Out
Для каждой рабочей роли Scale Out либо удалите рабочую роль и снова добавьте ее с помощью [диспетчера Scale Out](integration-services-ssis-scale-out-manager.md), либо выполните действия с 5.1 по 5.3 ниже:

5.1. Установите клиентский SSL-сертификат в корневое хранилище сертификатов локального компьютера на узле рабочей роли.

5.2. Обновите файл конфигурации службы рабочей роли Scale Out (\<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config) на узле рабочей роли. Обновите **MasterHttpsCertThumbprint**, используя отпечаток нового SSL-сертификата.

5.3. Перезапустите службу рабочей роли Scale Out.


## <a name="scale-out-worker-certificate"></a>Сертификат рабочей роли Scale Out

Сертификат рабочей роли Scale Out создается автоматически во время установки рабочей роли Scale Out. 

### <a name="change-scale-out-worker-certificate"></a>Изменение сертификата рабочей роли Scale Out

Если вам требуется изменить сертификат рабочей роли Scale Out, выполните описанные ниже действия.

#### <a name="1-create-a-certificate"></a>1. Создание сертификата
Создайте и установите сертификат с помощью следующей команды:
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Пример
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Установка клиентского сертификата в корневое хранилище сертификатов локального компьютера на узле рабочей роли

#### <a name="3-give-service-access-to-the-certificate"></a>3. Предоставление службе доступа к сертификату
Удалите старый сертификат и предоставьте службе рабочей роли Scale Out доступ к новому сертификату с помощью следующей команды:
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Пример
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Обновление файла конфигурации для рабочей роли Scale Out
Обновите файл конфигурации для службы рабочей роли Scale Out (\<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config) на узле рабочей роли. Обновите **WorkerHttpsCertThumbprint**, используя отпечаток нового сертификата.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Установка клиентского сертификата в корневое хранилище сертификатов локального компьютера на узле мастера

#### <a name="6-restart-scale-out-worker-service"></a>6. Перезапуск службы рабочей роли Scale Out
