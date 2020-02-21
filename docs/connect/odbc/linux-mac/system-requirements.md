---
title: Требования к системе (драйвер ODBC для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 49cb24120d6c476e5b03c4a0cad2ddda511a9360
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76911208"
---
# <a name="system-requirements"></a>Требования к системе
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Эта статья содержит требования для использования драйвера [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS.


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13, 13.1 и 17 for SQL Server

Драйверы Linux и macOS доступны только для 64-разрядных версий следующих операционных систем:

|Операционная система|Поддерживаемая версия драйвера|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13, 13.1, 17.4|
|Apple macOS 10.12 (Sierra)|13, 13.1, 17.4|
|Apple macOS 10.13 (High Sierra)|17 и выше| 
|Apple macOS 10.14 (Mojave)|17 и выше| 
|Apple macOS 10.15 (Catalina)|17.5 и выше| 
|Alpine Linux 3.11|17.5 и выше| 
|Debian Linux 8|13, 13.1, 17.4| 
|Debian Linux 9|17 и выше|
|Debian Linux 10|17.4 и выше|
|Oracle Linux 8|17.5 и выше|
|RedHat Enterprise Linux 6|13, 13.1, 17 и выше|
|RedHat Enterprise Linux 7|13, 13.1, 17 и выше|
|RedHat Enterprise Linux 8|17.4 и выше|
|SuSE Linux Enterprise Server 11|13, 13.1, 17 и выше <br /><br /> **ПРИМЕЧАНИЕ.** Драйвер ODBC версии 17 поддерживает только SuSE Linux Enterprise Server 11 SP4|
|SuSE Linux Enterprise Server 12|13, 13.1, 17 и выше|
|SUSE Linux Enterprise Server 15|17 и выше|
|Ubuntu Linux 14.04|13, 13.1, 17.4|
|Ubuntu Linux 15.10|13, 13.1|
|Ubuntu Linux 16.04|13, 13.1, 17 и выше|
|Ubuntu Linux 16.10|13, 13.1|
|Ubuntu Linux 17.04|17.4| 
|Ubuntu Linux 17.10|17.4|
|Ubuntu Linux 18.04|17 и выше|
|Ubuntu Linux 18.10|17.4|
|Ubuntu Linux 19.04|17.3|
|Ubuntu Linux 19.10|17.5 и выше| 

> [!NOTE]
> - Для операционных систем с активной поддержкой после версии драйвера отображается символ "+", а без символа плюса отображается последняя версия драйвера, поддерживаемая для соответствующей ОС.

Пакеты установки для [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13, 13.1 и 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS разрешают зависимости драйвера автоматически при установке с помощью системы управления пакетами дистрибутива, как описано в разделе [Установка драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Драйвер Microsoft ODBC 11 для SQL Server  
  
-   64-разрядный диспетчер драйверов UnixODBC 2.3.0, созданный для 64-разрядных SQLLEN/SQLULEN. Более поздние версии 64-разрядного диспетчера драйверов UnixODBC не поддерживаются для драйвера ODBC в Linux. Подробнее см. в разделе [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  
  
-   Драйвер ODBC для **Red Hat Enterprise Linux 5 (64-разрядная версия)** требует наличия следующих пакетов, и его можно скачать здесь: [Microsoft ODBC Driver 11 for SQL Server — Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Драйвер ODBC для **Red Hat Enterprise Linux 6 (64-разрядная версия)** требует наличия следующих пакетов, и его можно скачать здесь: [Microsoft ODBC Driver 11 for SQL Server — Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Драйвер ODBC для **SUSE Linux Enterprise 11 с пакетом обновления 2 (64-разрядная версия)** требует наличия следующих пакетов, и его можно скачать здесь: [Предварительная версия Microsoft ODBC Driver 11 for SQL Server — SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916)  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>См. также:
[Установка диспетчера драйверов](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
