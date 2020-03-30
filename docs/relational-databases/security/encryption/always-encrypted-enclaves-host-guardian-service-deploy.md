---
title: Развертывание службы защиты узла
description: Разверните службу защиты узла для Always Encrypted с безопасными анклавами.
ms.custom: ''
ms.date: 11/15/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: rpsqrd
ms.author: ryanpu
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6794f5fd57d1c89e7c1989e79b5072a8c15cf43e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "74320057"
---
# <a name="deploy-the-host-guardian-service-for-ssnoversion-md"></a>Развертывание службы защиты узла для [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]

[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

В этой статье описывается, как развернуть службу защиты узла (HGS) в качестве службы аттестации для [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)].
Прежде чем начать, ознакомьтесь с полным списком предварительных требований и рекомендаций по архитектуре в статье [Планирование аттестации службы защиты узла](./always-encrypted-enclaves-host-guardian-service-plan.md).

## <a name="step-1-set-up-the-first-hgs-computer"></a>Шаг 1. Настройка первого компьютера HGS

Служба защиты узла (HGS) выполняется как кластеризованная служба на одном или нескольких компьютерах.
На этом шаге вы настроите новый кластер HGS на первом компьютере.
Если у вас уже есть кластер HGS и вы добавляете к нему дополнительные компьютеры для обеспечения высокого уровня доступности, перейдите к разделу [Шаг 2. Добавление дополнительных компьютеров HGS в кластер](#step-2-add-more-hgs-computers-to-the-cluster).

Прежде чем начать, убедитесь в том, что используемый компьютер работает под управлением выпуска Windows Server 2019 Standard или Datacenter, у вас есть права локального администратора и компьютер еще не присоединен к домену Active Directory.

1. Войдите на первый компьютер HGS с правами локального администратора и откройте консоль Windows PowerShell с повышенными привилегиями. Выполните приведенную ниже команду, чтобы установить роль службы защиты узла. Компьютер автоматически перезагрузится для применения изменений.

    ```powershell
    Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
    ```

2. После перезагрузки компьютера HGS выполните следующие команды в консоли Windows PowerShell с повышенными привилегиями, чтобы установить новый лес Active Directory:

    ```powershell
    # Select the name for your new Active Directory root domain.
    # Make sure the name does not conflict with, and is not subordinate to, any existing domains on your network.
    $HGSDomainName = 'bastion.local'

    # Specify a Directory Services Restore Mode password that can be used to recover your domain in safe mode.
    # This password is not, and will not change, your admin account password.
    # Save this password somewhere safe and include it in your disaster recovery plan.
    $DSRMPassword = Read-Host -AsSecureString -Prompt "Directory Services Restore Mode Password"

    Install-HgsServer -HgsDomainName $HgsDomainName -SafeModeAdministratorPassword $DSRMPassword -Restart
    ```

    Компьютер HGS снова перезагрузится для завершения настройки леса Active Directory. При следующем входе в систему ваша учетная запись администратора станет учетной записью администратора домена. Для получения дополнительных сведений об управлении новым лесом и его защите рекомендуется ознакомиться с [документацией по операциям в доменных службах Active Directory](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/component-updates/ad-ds-operations).

3. Далее вы настроите кластер HGS и установите службу аттестации, выполнив следующую команду в консоли Windows PowerShell с повышенными привилегиями:

    ```powershell
    # Note: the name you provide here will be shared by all HGS nodes and used to point your SQL Server computers to the HGS cluster.
    # For example, if you provide "attsvc" here, a DNS record for "attsvc.yourdomain.com" will be created for every HGS computer.
    Initialize-HgsAttestation -HgsServiceName 'hgs'
    ```

## <a name="step-2-add-more-hgs-computers-to-the-cluster"></a>Шаг 2. Добавление дополнительных компьютеров HGS в кластер

После настройки первого компьютера и кластера HGS можно добавить дополнительные серверы HGS, чтобы обеспечить высокий уровень доступности.
Если вы настраиваете только один сервер HGS (например, в среде разработки и тестирования), можно перейти к шагу 3.

Так же, как и в случае с первым компьютером HGS, убедитесь в том, что присоединяемый к кластеру компьютер работает под управлением выпуска Windows Server 2019 Standard или Datacenter, у вас есть права локального администратора и компьютер еще не присоединен к домену Active Directory.

1. Войдите на компьютер с правами локального администратора и откройте консоль Windows PowerShell с повышенными привилегиями. Выполните приведенную ниже команду, чтобы установить роль службы защиты узла. Компьютер автоматически перезагрузится для применения изменений.

    ```powershell
    Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
    ```

2. Проверьте конфигурацию клиента DNS на компьютере, чтобы убедиться в возможности разрешения домена HGS. Приведенная ниже команда должна вернуть IP-адрес сервера HGS. Если домен HGS разрешить не удается, может потребоваться обновить сведения о DNS-сервере в сетевом адаптере, чтобы для разрешения имен использовался DNS-сервер HGS.

    ```powershell
    # Change 'bastion.local' to the domain name you specified in Step 1.2
    nslookup bastion.local

    # If it fails, use sconfig.exe, option 8, to set the first HGS computer as your preferred DNS server.
    ```

3. После перезагрузки компьютера выполните приведенную ниже команду в консоли Windows PowerShell с повышенными привилегиями, чтобы присоединить компьютер к домену Active Directory, созданному первым сервером HGS. Для выполнения этой команды потребуются учетные данные администратора домена AD. После выполнения команды компьютер перезагрузится и станет контроллером домена Active Directory для домена HGS.

    ```powershell
    # Provide the fully qualified HGS domain name
    $HGSDomainName = 'bastion.local'

    # Provide a domain administrator's credential for the HGS domain
    $DomainAdminCred = Get-Credential

    # Specify a Directory Services Restore Mode password that can be used to recover your domain in safe mode.
    # This password is not, and will not change, your admin account password.
    # Save this password somewhere safe and include it in your disaster recovery plan.
    $DSRMPassword = Read-Host -AsSecureString -Prompt "Directory Services Restore Mode Password"

    Install-HgsServer -HgsDomainName $HgsDomainName -HgsDomainCredential $DomainAdminCred -SafeModeAdministratorPassword $DSRMPassword -Restart
    ```

4. После перезагрузки компьютера войдите в систему с учетными данными администратора домена. Откройте консоль Windows PowerShell с повышенными привилегиями и выполните приведенные ниже команды, чтобы настроить службу аттестации. Так как служба аттестации поддерживает кластер, она реплицирует свою конфигурацию из других членов кластера. Изменения, вносимые в политики аттестации в любом узле HGS, применяются ко всем остальным узлам.

    ```powershell
    # Provide the IP address of an existing, initialized HGS server
    # If you are using separate networks for cluster and application traffic, choose an IP address on the cluster network.
    # You can find the IP address of your HGS server by signing in and running "ipconfig /all"
    Initialize-HgsAttestation -HgsServerIPAddress '172.16.10.20'
    ```

5. Повторите шаг 2 для каждого компьютера, который нужно добавить в кластер HGS.

## <a name="step-3-configure-a-dns-forwarder-to-your-hgs-cluster"></a>Шаг 3. Настройка переадресации DNS в кластер HGS

Служба HGS использует собственный DNS-сервер, который содержит записи имен, необходимые для разрешения службы аттестации.
Ваши компьютеры SQL Server не смогут разрешать эти записи, пока вы не настроите перенаправление запросов с DNS-сервера в своей сети на DNS-серверы HGS.

Процесс настройки переадресации DNS зависит от поставщика, поэтому мы рекомендуем обратиться к администратору сети за конкретными инструкциями.

Если в корпоративной сети используется роль DNS-сервера Windows Server, администратор DNS может создать сервер условной пересылки в домен HGS, чтобы перенаправлялись только запросы к домену HGS.
Например, если серверы HGS используют доменное имя bastion.local и имеют IP-адреса 172.16.10.20, 172.16.10.21 и 172.16.10.22, можно выполнить следующую команду на корпоративном DNS-сервере, чтобы настроить сервер условной пересылки:

```powershell
# Tip: make sure to provide every HGS server's IP address
# If you use separate NICs for cluster and application traffic, use the application traffic NIC IP addresses here
Add-DnsServerConditionalForwarderZone -Name 'bastion.local' -ReplicationScope "Forest" -MasterServers "172.16.10.20", "172.16.10.21", "172.16.10.22"
```

## <a name="step-4-configure-the-attestation-service"></a>Шаг 4. Настройка службы аттестации

HGS поддерживает два режима аттестации: аттестацию TPM для криптографической проверки целостности и подлинности каждого компьютера [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] и аттестацию ключа узла для простой проверки подлинности компьютера [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)].
Если вы еще не выбрали режим аттестации, ознакомьтесь со сведениями об аттестации в [руководстве по планированию](./always-encrypted-enclaves-host-guardian-service-plan.md#attestation-modes), чтобы узнать больше о гарантиях безопасности и вариантах использования каждого режима.

Инструкции в этом разделе служат для настройки базовых политик аттестации для конкретного режима аттестации.
Сведения о конкретном узле будут зарегистрированы в шаге 4.
Если в будущем потребуется изменить режим аттестации, повторите шаги 3 и 4, используя нужный режим аттестации.

### <a name="switch-to-tpm-attestation"></a>Переключение на аттестацию TPM

Чтобы настроить аттестацию TPM в HGS, потребуется компьютер с доступом к Интернету и по крайней мере один компьютер [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] с микросхемой TPM 2.0 ред. 1.16.

Чтобы настроить режим TPM для HGS, откройте консоль PowerShell с повышенными привилегиями и выполните следующую команду:

```powershell
Set-HgsServer -TrustTpm
```

Все компьютеры HGS в кластере теперь будут использовать режим TPM, когда компьютер [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] будет пытаться пройти аттестацию.

Прежде чем регистрировать данные TPM с компьютеров SQL Server в службе HGS, необходимо установить корневые сертификаты ключа подтверждения (EK) от поставщиков модулей TPM.
Каждый физический модуль TPM настраивается в фабрике с уникальным ключом подтверждения, к которому прилагается сертификат ключа подтверждения, определяющий изготовителя.
Этот сертификат гарантирует подлинность модуля TPM.
HGS проверяет сертификат ключа подтверждения при регистрации нового модуля TPM в HGS, сравнивая цепочку сертификатов со списком доверенных корневых сертификатов.

Корпорация Майкрософт публикует список корневых сертификатов известных поставщиков TPM, который можно импортировать в хранилище корневых сертификатов надежных модулей TPM для службы HGS.
Если компьютеры SQL Server виртуализированы, необходимо обратиться к поставщику облачных служб или поставщику платформы виртуализации, чтобы узнать, как получить цепочку сертификатов для ключа подтверждения виртуального модуля TPM.

Чтобы скачать пакет корневых сертификатов для надежных физических модулей TPM от корпорации Майкрософт, выполните указанные ниже действия.

1. На компьютере с доступом к Интернету скачайте последнюю версию пакета корневых сертификатов для модулей TPM со страницы [https://go.microsoft.com/fwlink/?linkid=2097925](https://go.microsoft.com/fwlink/?linkid=2097925).

2. Проверьте подпись CAB-файла, чтобы убедиться в его подлинности.

    ```powershell
    # Note: replace the path below with the correct one to the file you downloaded in step 1
    Get-AuthenticodeSignature ".\TrustedTpm.cab"
    ```

    > [!WARNING]
    > Если подпись недействительна, прервите процедуру и обратитесь за помощью в службу поддержки Майкрософт.

3. Разверните CAB-файл в новом каталоге.

    ```powershell
    mkdir .\TrustedTpmCertificates
    expand.exe -F:* ".\TrustedTpm.cab" ".\TrustedTpmCertificates"
    ```

4. В новом каталоге будут присутствовать каталоги для каждого поставщика TPM. Ненужные каталоги можно удалить.

5. Скопируйте весь каталог TrustedTpmCertificates на сервер HGS.

6. Откройте консоль PowerShell с повышенными привилегиями на сервере HGS и выполните следующую команду, чтобы импортировать все корневые и промежуточные сертификаты TPM:

    ```powershell
    # Note: replace the path below with the correct location of the TrustedTpmCertificates folder on your HGS computer
    cd "C:\scratch\TrustedTpmCertificates"
    .\setup.cmd
    ```

7. Повторите шаги 5 и 6 для каждого компьютера HGS.

Если вы получили промежуточные и корневые сертификаты ЦС от изготовителя оборудования, поставщика облачных служб или поставщика платформы виртуализации, можно напрямую импортировать сертификаты в соответствующее хранилище сертификатов на локальном компьютере: `TrustedHgs_RootCA` или `TrustedHgs_IntermediateCA`. Например, в PowerShell выполните следующую команду:

```powershell
# Imports MyCustomTpmVendor_Root.cer to the local machine's "TrustedHgs_RootCA" store
Import-Certificate -FilePath ".\MyCustomTpmVendor_Root.cer" -CertStoreLocation "Cert:\LocalMachine\TrustedHgs_RootCA"
```

### <a name="switch-to-host-key-attestation"></a>Переключение на аттестацию ключа узла

Чтобы использовать аттестацию ключа узла, на сервере HGS в консоли PowerShell с повышенными привилегиями выполните следующую команду:

```powershell
Set-HgsServer -TrustHostKey
```

Все компьютеры HGS в кластере теперь будут использовать режим ключа узла, когда компьютер [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] будет пытаться пройти аттестацию.

## <a name="step-5-configure-the-hgs-https-binding"></a>Шаг 5. Настройка привязки HTTPS для службы HGS

При установке по умолчанию HGS предоставляет только привязку HTTP (порт 80).
Вы можете настроить привязку HTTPS (порт 443) для шифрования всех данных, передаваемых между компьютерами [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] и HGS.
Привязка HTTPS рекомендуется для всех рабочих экземпляров HGS.

1. Получите сертификат TLS от центра сертификации, используя полное имя службы HGS из шага 1.3 в качестве имени субъекта. Если имя службы неизвестно, его можно узнать, выполнив командлет `Get-HgsServer` на любом компьютере HGS. Вы можете добавить альтернативные DNS-имена в список альтернативных имен субъектов, если компьютеры [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] используют другое DNS-имя для доступа к кластеру HGS (например, если служба HGS находится за подсистемой балансировки сетевой нагрузки с другим адресом).

2. На компьютере HGS используйте командлет [Set-HgsServer](https://docs.microsoft.com/powershell/module/hgsserver/set-hgsserver), чтобы включить привязку HTTPS и указать сертификат TLS, полученный на предыдущем шаге. Если сертификат уже установлен в локальном хранилище сертификатов на компьютере, используйте следующую команду, чтобы зарегистрировать его в службе HGS:

    ```powershell
    # Note: you'll need to know the thumbprint for your certificate to configure HGS this way
    Set-HgsServer -Http -Https -HttpsCertificateThumbprint "54A043386555EB5118DB367CFE38776F82F4A181"
    ```

    Если вы экспортировали сертификат (с закрытым ключом) в защищенный паролем PFX-файл, его можно зарегистрировать в службе HGS, выполнив следующую команду:

    ```powershell
    $PFXPassword = Read-Host -AsSecureString -Prompt "PFX Password"
    Set-HgsServer -Http -Https -HttpsCertificatePath "C:\path\to\hgs_tls.pfx" -HttpsCertificatePassword $PFXPassword
    ```

3. Повторите шаги 1 и 2 для каждого компьютера HGS в кластере. Сертификаты TLS не реплицируются автоматически между узлами HGS. Кроме того, каждый компьютер HGS может иметь собственный уникальный сертификат TLS, если имя субъекта совпадает с именем службы HGS.

## <a name="next-steps"></a>Дальнейшие действия

- [Регистрация компьютеров в службе HGS](./always-encrypted-enclaves-host-guardian-service-register.md)
