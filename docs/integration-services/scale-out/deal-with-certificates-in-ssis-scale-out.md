---
title: Управление сертификатами для SQL Server Integration Services Scale Out | Документы Майкрософт
ms.description: This article describes how to manage certificates to secure communications between SSIS Scale Out Master and Scale Out Workers.
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.custom: performance
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: 6c90b71ed61deeadbc0af2592f137893fa676a05
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67896963"
---
# <a name="manage-certificates-for-sql-server-integration-services-scale-out"></a>Управление сертификатами для SQL Server Integration Services Scale Out

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Для защиты обмена данными между мастером Scale Out и рабочими ролями Scale Out в SSIS Scale Out используются два сертификата: один для мастера, а другой для рабочих ролей. 

## <a name="scale-out-master-certificate"></a>Сертификат мастера Scale Out

В большинстве случаев сертификат мастера Scale Out настраивается во время установки мастера Scale Out.

На странице **Настройка развертывания служб Integration Services — главный узел** мастера установки SQL Server вы можете создать самозаверяющий SSL-сертификат или воспользоваться существующим.

![Конфигурация мастера](media/master-config.PNG)

**Новый сертификат**. Если у вас нет особых требований к сертификатам, можно создать самозаверяющий SSL-сертификат. Для него можно дополнительно указать общие имена. Не забудьте включить в их число имя узла конечной точки мастера, которую потом будут использовать рабочие роли Scale Out. По умолчанию включаются имя компьютера и IP-адрес узла мастера. 

**Существующий сертификат**. Если вы решили использовать существующий сертификат, нажмите кнопку **Обзор**, чтобы выбрать SSL-сертификат из **корневого** хранилища сертификатов на локальном компьютере.

### <a name="change-the-scale-out-master-certificate"></a>Изменение сертификата мастера Scale Out

Вам может потребоваться сменить сертификат мастера Scale Out из-за истечения срока действия сертификата или по другим причинам. Чтобы сменить сертификат мастера Scale Out, выполните указанные ниже действия.

#### <a name="1-create-an-ssl-certificate"></a>1. Создание SSL-сертификата.
Создайте и установите SSL-сертификат в узле мастера с помощью следующей команды:

```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine -a sha1
```
Пример:

```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine -a sha1
```

#### <a name="2-bind-the-certificate-to-the-master-port"></a>2. Привязка сертификата к порту мастера
Проверьте исходную привязку с помощью следующей команды:

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

Пример:

```dos
netsh http show sslcert ipport=0.0.0.0:8391
```

Удалите исходные привязки и настройте новую с помощью следующих команд:

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```

Пример:

```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```

#### <a name="3-update-the-scale-out-master-service-configuration-file"></a>3. Обновление файла конфигурации для службы мастера Scale Out
Обновите файл конфигурации для службы мастера Scale Out (`\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`) в узле мастера. Обновите **SSLCertThumbprint**, используя отпечаток нового SSL-сертификата.

#### <a name="4-restart-the-scale-out-master-service"></a>4. Перезапуск службы мастера Scale Out

#### <a name="5-reconnect-scale-out-workers-to-scale-out-master"></a>5. Повторное подключение рабочих ролей Scale Out к мастеру Scale Out
Для каждой рабочей роли Scale Out либо удалите рабочую роль и снова добавьте ее с помощью [диспетчера Scale Out](integration-services-ssis-scale-out-manager.md), либо выполните указанные ниже действия.

а.  Установите SSL-сертификат клиента в корневое хранилище локального компьютера в узле рабочей роли.

b.  Обновите файл конфигурации для службы рабочей роли Scale Out.

Обновите файл конфигурации для службы рабочей роли Scale Out (`\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config`) в узле рабочей роли. Обновите **MasterHttpsCertThumbprint**, используя отпечаток нового SSL-сертификата.

c.  Перезапустите службу рабочей роли Scale Out.

## <a name="scale-out-worker-certificate"></a>Сертификат рабочей роли Scale Out

Сертификат рабочей роли Scale Out создается автоматически во время установки рабочей роли Scale Out. 

### <a name="change-the-scale-out-worker-certificate"></a>Смена сертификата рабочей роли Scale Out

Если требуется сменить сертификат рабочей роли Scale Out, выполните указанные ниже действия.

#### <a name="1-create-a-certificate"></a>1. Создание сертификата
Создайте и установите сертификат с помощью следующей команды:

```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```

Пример:

```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```

#### <a name="2-install-the-client-certificate-to-the-root-store-of-the-local-computer-on-the-worker-node"></a>2. Установка сертификата клиента в корневое хранилище локального компьютера в узле рабочей роли

#### <a name="3-grant-service-access-to-the-certificate"></a>3. Предоставление службе доступа к сертификату
Удалите старый сертификат и предоставьте службе рабочей роли Scale Out доступ к новому сертификату с помощью следующей команды:

```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```

Пример:

```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```

#### <a name="4-update-the-scale-out-worker-service-configuration-file"></a>4. Обновление файла конфигурации для службы рабочей роли Scale Out
Обновите файл конфигурации для службы рабочей роли Scale Out (`\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config`) в узле рабочей роли. Обновите **WorkerHttpsCertThumbprint**, используя отпечаток нового сертификата.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-the-local-computer-on-the-master-node"></a>5. Установка сертификата клиента в корневое хранилище локального компьютера в узле Master

#### <a name="6-restart-the-scale-out-worker-service"></a>6. Перезапуск службы рабочей роли Scale Out

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения см. в следующих статьях:
-   [Главная роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
-   [Рабочая роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
