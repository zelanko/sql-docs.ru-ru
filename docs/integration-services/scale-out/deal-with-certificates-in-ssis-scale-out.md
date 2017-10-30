---
title: "Работать с сертификатами в Sql Server Integration Services масштабное развертывание | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2970b2b2cc7cf30c18a203ebbb92b5418bfc9be5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Работать с сертификатами в SQL Server Integration Services масштабное развертывание

Для защиты соединения между шкалы Out главного и масштаб Out рабочих, два сертификаты используются в масштабное развертывание, т. е. масштаб Out главного сертификат и сертификат шкалы ожидания рабочего процесса. 

## <a name="scale-out-master-certificate"></a>Масштаб Out главного сертификата

В большинстве случаев сертификат шкалы Out Master настраивается во время установки масштаба Out Master.

В **конфигурации Integration Services шкалы Out - главного узла** страницы мастера установки SQL Server, вы можете создать новый самозаверяющий сертификат SSL или использовать существующий сертификат SSL.

![Образец конфигурации](media/master-config.PNG)

Если на сертификаты нет особых требований, можно создать самозаверяющий сертификат SSL. Можно уточнить, общих имен в сертификате. Убедитесь, что имя узла master конечная точка, используемая шкалы ожидания рабочим процессом позже включается в общих имен. По умолчанию включены имя компьютера и IP-адрес главного узла. 

Если вы решили использовать существующий сертификат, нажмите кнопку «Обзор...», чтобы выбрать сертификат SSL **корневой** хранилище сертификатов локального компьютера.

### <a name="change-scale-out-master-certificate"></a>Изменение масштаба Out главного сертификата

Может потребоваться изменить масштаб Out Master сертификат из-за истечения срока действия сертификата или по другим причинам. Выполните следующие действия:

#### <a name="1-create-a-ssl-certificate"></a>1. Создайте сертификат SSL.
Создание и установка SSL-сертификат на главный узел с помощью следующей команды:
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Пример
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Привяжите сертификат к основной порт
Проверьте исходные привязки с помощью команды:
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Пример
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Удалить исходное привязки и настроить новую привязку с помощью следующих команд:
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Пример
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Обновить файл конфигурации службы шкалы Out Master
Обновление файла конфигурации службы шкалы Out Master, \<драйвер\>: \Program Files\Microsoft Server\140\DTS\Binn\MasterSettings.config SQL, на основной узел. Обновление **SSLCertThumbprint** отпечаток нового сертификата SSL.

#### <a name="4-restart-scale-out-master-service"></a>4. Перезапустите службу шкалы Out Master

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Повторное подключение масштабирования рабочей масштабное развертывание образца
Для каждой шкалы ожидания рабочего процесса, либо удалить рабочий процесс, а затем добавьте его с [шкалы ожидания диспетчера](integration-services-ssis-scale-out-manager.md) или выполните действия 5.1 для 5.3 ниже:

5.1 Установите клиентский SSL-сертификат в корневое хранилище сертификатов локального компьютера на рабочий узел

5.2 обновление масштаба Out рабочих службы конфигурации файла обновления шкалы ожидания рабочий файл конфигурации службы, \<драйвер\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config на рабочий узел. Обновление **MasterHttpsCertThumbprint** отпечаток нового сертификата SSL.

5.3 перезапустите шкалы ожидания службы рабочей роли


## <a name="scale-out-worker-certificate"></a>Сертификат шкалы ожидания рабочего процесса

Сертификат шкалы ожидания рабочего процесса создается автоматически во время установки масштаба ожидания рабочего процесса. 

### <a name="change-scale-out-worker-certificate"></a>Изменение масштаба исходящий сертификат рабочего процесса

В случаях, необходимо изменить сертификат шкалы ожидания рабочего процесса выполните следующие действия.

#### <a name="1-create-a-certificate"></a>1. Создание сертификата
Создайте и установите сертификат с помощью следующей команды:
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Пример
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Установить клиентский сертификат в корневое хранилище сертификатов локального компьютера на рабочий узел

#### <a name="3-give-service-access-to-the-certificate"></a>3. Предоставить доступ к службе для сертификата
Удалить старый сертификат и предоставляйте доступ службы шкалы Out работника на новый сертификат с помощью команды:
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Пример
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Обновить файл конфигурации шкалы Out работника
Файл конфигурации службы обновления шкалы Out работника, \<драйвер\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config на рабочий узел. Обновление **WorkerHttpsCertThumbprint** отпечаток нового сертификата.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Установить клиентский сертификат в корневое хранилище сертификатов локального компьютера на основной узел

#### <a name="6-restart-scale-out-worker-service"></a>6. Перезапустите службу шкалы Out работника

