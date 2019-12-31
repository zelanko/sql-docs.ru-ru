---
title: Настройка TLS 1,2
description: Рекомендация по настройке TLS 1,2 в ТД
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 988cac765a596b541d128b0b6190f6f228d95ee7
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401255"
---
# <a name="configure-tls-12-in-aps"></a>Настройка TLS 1,2 в ТД

Чтобы защитить ТД только с помощью TLS 1,2, необходимо явно отключить другой протокол на всех физических и виртуальных узлах. Для отключения протоколов требуется изменение параметров реестра. Изменения в реестре потребует перезагрузки виртуальных и физических узлов.

> [!WARNING]
> Настоящий раздел, метод или задача содержит шаги, в которых указано, как внести изменения в реестр. Однако при неправильном изменении реестра могут возникнуть серьезные проблемы, которые могут привести к потере данных и потребовать переустановки операционной системы. Перед изменением реестра настоятельно рекомендуется создать его резервную копию. Тогда в случае возникновения проблем реестр можно будет восстановить. Чтобы получить дополнительные сведения о резервном копировании и восстановлении реестра, щелкните следующий номер статьи базы знаний Майкрософт:<br>
[322756](https://support.microsoft.com/help/322756) . Резервное копирование и восстановление реестра в Windows

**Включен**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Также задайте следующие ключи на клиентских компьютерах, где установлены такие инструменты, как адаптеры назначения служб SQL Server APS.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



