---
title: Устранение неполадок в работе SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье описывается устранение распространенных неполадок в SSIS Scale Out.
ms.custom: performance
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: 87f5ab815fc7d3a5df23aa3675e92ffa206bfcdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896152"
---
# <a name="troubleshoot-scale-out"></a>Устранение неполадок Scale Out

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Работа SSIS Scale Out строится на взаимодействии между базой данных каталога SSIS (`SSISDB`), службой мастера Scale Out и службой рабочей роли Scale Out. В некоторых случаях это взаимодействие может быть нарушено из-за ошибок конфигурации, нехватки разрешений на доступ или по другим причинам. В этой статье приводятся рекомендации по устранению неполадок с конфигурацией Scale Out.

Чтобы определить симптомы возникших проблем, последовательно выполните приведенные ниже действия, пока проблема не будет решена.

## <a name="scale-out-master-fails"></a>Сбой мастера Scale Out

### <a name="symptoms"></a>Симптомы 
-   Мастеру Scale Out не удается подключиться к SSISDB. 

-   Свойства мастера не отображаются в диспетчере Scale Out.

-   Свойства мастера не заполнены в представлении `[catalog].[master_properties]`.

### <a name="solution"></a>Решение
1.  Убедитесь в том, что компонент Scale Out включен.

    В SQL Server Management Studio в обозревателе объектов щелкните правой кнопкой мыши узел **SSISDB** и установите флажок **Scale Out разрешен**.

    ![Включен ли режим Scale Out](media/isenabled.PNG)

    Если это свойство имеет значение False, включите Scale Out, вызвав хранимую процедуру `[catalog].[enable_scaleout]`.

2.  Проверьте правильность имени SQL Server, указанного в файле конфигурации мастера Scale Out, и перезапустите службу мастера Scale Out.

## <a name="scale-out-worker-fails"></a>Сбой рабочей роли Scale Out

### <a name="symptoms"></a>Симптомы 
-   Рабочей роли Scale Out не удается подключиться к мастеру Scale Out.

-   Рабочая роль Scale Out не отображается после ее добавления в диспетчере Scale Out.

-   Рабочая роль Scale Out не отображается в представлении `[catalog].[worker_agents]`.

-   Служба рабочей роли Scale Out выполняется, хотя рабочая роль Scale Out отключена.

### <a name="solution"></a>Решение
Проверьте сообщения об ошибках в журнале службы рабочей роли Scale Out по пути `\<drive\>:\Users\\*[account running worker service]*\AppData\Local\SSIS\Cluster\Agent`.

## <a name="no-endpoint-listening"></a>Нет конечной точки, ожидающей передачи данных

### <a name="symptoms"></a>Симптомы

*"System.ServiceModel.EndpointNotFoundException: Прослушивание на https://* [имя_компьютера]:[порт] */ClusterManagement/ не выполняла ни одна конечная точка, которая могла бы принять сообщение".*

### <a name="solution"></a>Решение

1.  Проверьте правильность номера порта, указанного в файле конфигурации службы мастера Scale Out, и перезапустите службу мастера Scale Out. 

2.  Проверьте правильность конечной точки мастера, указанной в файле конфигурации службы рабочей роли Scale Out, и перезапустите службу рабочей роли Scale Out.

3.  Проверьте, открыт ли порт брандмауэра в узле мастера Scale Out.

4.  Устраните любые другие проблемы с подключением между узлом мастера Scale Out и узлом рабочей роли Scale Out.

## <a name="could-not-establish-trust-relationship"></a>Не удалось установить доверительные отношения

### <a name="symptoms"></a>Симптомы
*"System.ServiceModel.Security.SecurityNegotiationException. Не удалось установить отношения доверия для защищенного канала SSL/TLS с полномочиями "[имя_компьютера]:[порт]"".*

*"System.Net.WebException. Базовое соединение закрыто: Не удалось установить доверительные отношения для защищенного канала SSL/TLS".*

*"System.Security.Authentication.AuthenticationException. Удаленный сертификат недопустим согласно процедуре проверки".*

### <a name="solution"></a>Решение
1.  Установите сертификат мастера Scale Out в корневое хранилище сертификатов локального компьютера в узле рабочей роли Scale Out (если он не установлен) и перезапустите службу рабочей роли Scale Out.

2.  Убедитесь в том, что имя узла в конечной точке мастера включено в номера CN сертификата мастера Scale Out. В противном случае сбросьте конечную точку мастера в файле конфигурации рабочей роли Scale Out и перезапустите службу рабочей роли Scale Out. 

    > [!NOTE]
    > Если изменить имя узла конечной точки мастера не удается из-за настроек DNS, необходимо изменить сертификат мастера Scale Out. См. статью [Работа с сертификатами в SQL Server Integration Services (SSIS) Scale Out](deal-with-certificates-in-ssis-scale-out.md).

3.  Убедитесь в том, что отпечаток мастера в конфигурации рабочей роли Scale Out совпадает с отпечатком в сертификате мастера Scale Out. 

## <a name="could-not-establish-secure-channel"></a>Не удалось установить безопасный канал

### <a name="symptoms"></a>Симптомы

*"System.ServiceModel.Security.SecurityNegotiationException. Не удалось установить безопасный канал для SSL/TLS с полномочиями "[имя_компьютера]:[порт]"".*

*"System.Net.WebException. Запрос был прерван: не удалось создать защищенный канал SSL/TLS".*

### <a name="solution"></a>Решение
С помощью приведенной ниже команды убедитесь в том, что ученая запись, с которой выполняется служба рабочей роли Scale Out, имеет доступ к сертификату рабочей роли Scale Out.

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

Если у учетной записи нет доступа, предоставьте ей соответствующие права с помощью приведенной ниже команды и перезапустите рабочую службу Scale Out.

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

## <a name="http-request-forbidden"></a>Запрос HTTP запрещен

### <a name="symptoms"></a>Симптомы

*"System.ServiceModel.Security.MessageSecurityException. Запрос HTTP запрещен для схемы проверки подлинности клиентов "Анонимно"".*

*"System.Net.WebException. Удаленный сервер вернул ошибку: (403) Запрещено".*

### <a name="solution"></a>Решение
1.  Установите сертификат рабочей роли Scale Out в корневое хранилище сертификатов локального компьютера в узле мастера Scale Out (если он не установлен) и перезапустите службу рабочей роли Scale Out.

2.  Выполните очистку ненужных сертификатов в корневом хранилище сертификатов локального компьютера в узле мастера Scale Out.

3.  Настройте Schannel, запретив отправку списка доверенных корневых центров сертификации в процессе подтверждения TLS/SSL. Для этого добавьте приведенный ниже параметр реестра в узле мастера Scale Out.

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL`

    Имя параметра: **SendTrustedIssuerList** 

    Тип параметра: **REG_DWORD** 

    Значение параметра: **0 (False)**

4.  Если не удается очистить все сертификаты, которые не являются самозаверяющими в шаге 2, присвойте значение 2 указанному ниже параметру реестра.

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL`

    Имя параметра: **ClientAuthTrustMode** 

    Тип параметра: **REG_DWORD** 

    Значение параметра: **2**

    > [!NOTE]
    > Если у вас нет самозаверяющих сертификатов в корневом хранилище сертификатов, аутентификация клиентского сертификата клиента завершится сбоем. См. дополнительные сведения о том, как [службы Internet Information Services (IIS) 8 могут отклонять запросы клиентских сертификатов с ошибками HTTP 403.7 или 403.16](https://support.microsoft.com/help/2802568/internet-information-services-iis-8-may-reject-client-certificate-requ).

## <a name="http-request-error"></a>Ошибка HTTP-запроса

### <a name="symptoms"></a>Симптомы

*"System.ServiceModel.CommunicationException. Произошла ошибка при создании HTTP-запроса к https://[имя_компьютера]:[порт]/ClusterManagement/. Это может быть связано с тем, что сертификат сервера неправильно настроен с использованием HTTP.SYS для варианта HTTPS. Кроме того, это может быть вызвано несоответствием привязки безопасности между клиентом и сервером."*

### <a name="solution"></a>Решение
1.  Убедитесь в том, что сертификат мастера Scale Out надлежащим образом привязан к порту в конечной точке мастера в узле мастера, выполнив приведенную ниже команду.

    ```dos
    netsh http show sslcert ipport=0.0.0.0:{Master port}
    ```

    Убедитесь в том, что отображаемое значение хэша сертификата соответствует отпечатку сертификата мастера Scale Out. Если привязка некорректна, сбросьте ее с помощью приведенных ниже команд и перезапустите службу рабочей роли Scale Out.

    ```dos
    netsh http delete sslcert ipport=0.0.0.0:{Master port}
    netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root  appid={random guid}
    ```

## <a name="cannot-open-certificate-store"></a>Невозможно открыть хранилище сертификатов

### <a name="symptoms"></a>Симптомы
Проверка при подключении рабочей роли Scale Out к мастеру Scale Out в диспетчере Scale Out завершается сбоем с сообщением об ошибке *"Невозможно открыть хранилище сертификатов на компьютере".*

### <a name="solution"></a>Решение

1.  Запустите диспетчер Scale Out от имени администратора. Если вы открываете его с помощью среды SQL Server Management Studio, необходимо запускать эту среду от имени администратора.

2.  Запустите службу удаленного реестра на компьютере (если она не запущена).

## <a name="execution-doesnt-start"></a>Не начинается выполнение

### <a name="symptoms"></a>Симптомы
Не начинается выполнение в Scale Out.

### <a name="solution"></a>Решение

Проверьте состояние компьютеров, которые выбраны для выполнения пакета в представлении `[catalog].[worker_agents]`. Должна быть активна и подключена как минимум одна рабочая роль.

## <a name="no-log"></a>Нет журнала

### <a name="symptoms"></a>Симптомы 
Пакеты успешно выполняются, однако в журнал не записываются сообщения.

### <a name="solution"></a>Решение

Убедитесь в том, что в экземпляре SQL Server, где размещается SSISDB, разрешена проверка подлинности SQL Server.

> [!NOTE]  
> Если вы изменили учетную запись для ведения журнала Scale Out, см. раздел [Изменение учетной записи для ведения журнала Scale Out](change-logdb-account.md) и проверьте строку подключения, используемую для ведения журнала.

## <a name="error-messages-arent-helpful"></a>Сообщений об ошибках недостаточно

### <a name="symptoms"></a>Симптомы
Сообщений об ошибках в отчете о выполнении пакета недостаточно для устранения неполадок.

### <a name="solution"></a>Решение
Дополнительные журналы выполнения можно найти в папке `TasksRootFolder`, настроенной в файле `WorkerSettings.config`. По умолчанию это папка `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Tasks`. Здесь *[учетная_запись]*  — это учетная запись, с которой выполняется служба рабочей роли Scale Out (по умолчанию `SSISScaleOutWorker140`).

Чтобы найти журнал выполнения пакета с идентификатором *[ИД_выполнения]* , выполните приведенную ниже команду Transact-SQL и получите *[ИД_задачи]* . Затем найдите вложенную папку с именем *[ИД_задачи]* в папке `TasksRootFolder`.

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```

> [!WARNING]
> Этот запрос предназначен исключительно для устранения неполадок. Внутренние представления, указанные в запросе, будут изменены в будущем. 

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в следующих статьях, посвященных установке и настройке SSIS Scale Out:
-   [Начало работы с SSIS Scale Out на одном компьютере](get-started-with-ssis-scale-out-onebox.md)
-   [Пошаговое руководство. Настройка Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md)
