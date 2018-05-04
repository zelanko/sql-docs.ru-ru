---
title: Требования к системе (драйвер ODBC для SQL Server) | Документы Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb3ccdb0348cc05146bdadbccb8ce26d733cea79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements"></a>Требования к системе
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этом разделе перечислены требования для использования [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux и macOS.


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13, 13.1 и 17 для SQL Server

Драйверы Linux и macOS доступны только для 64-разрядных версиях операционных систем:

|Операционная система|Поддерживаемые версии|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13, 13.1, 17|
|Apple macOS 10.12 (Сьерра)|13, 13.1, 17|
|Apple macOS 10.13 (высокая Сьерра)|17| 
|Debian Linux 8|13, 13.1, 17|
|Debian Linux 9|17|
|RedHat Enterprise Linux 6|13, 13.1, 17|
|RedHat Enterprise Linux 7|13, 13.1, 17|
|SuSE Linux Enterprise Server 11|13, 13.1, 17 <br /><br /> **Примечание:** 17 драйвер ODBC поддерживает только SuSE Linux Enterprise Server 11 SP4|
|SuSE Linux Enterprise Server 12|13, 13.1, 17|
|Ubuntu Linux 14.04|13, 13.1, 17|
|Ubuntu Linux 15.10|13, 13.1|
|Ubuntu Linux 16.04|13, 13.1, 17|
|Ubuntu Linux 16.10|13, 13.1|
|Ubuntu Linux 17.10|17|

Пакеты установки для [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвера ODBC 13, 13.1 и 17 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux и macOS разрешать зависимости драйвер автоматически, когда установлен в системе пакет управления дистрибутива, как описано в [ Установка драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Драйвер Microsoft ODBC 11 для SQL Server  
  
-   64-разрядный диспетчер драйверов UnixODBC 2.3.0, созданный для 64-разрядных SQLLEN/SQLULEN. Более поздние версии 64-разрядного диспетчера драйверов UnixODBC не поддерживаются для драйвера ODBC в Linux. Подробнее см. в разделе [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  
  
-   Драйвер ODBC для **Red Hat Enterprise Linux 5 (64-разрядная версия)** требует наличия следующих пакетов и может быть загружен здесь: [Microsoft ODBC Driver 11 for SQL Server — Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Драйвер ODBC для **Red Hat Enterprise Linux 6 (64-разрядная версия)** требует наличия следующих пакетов и может быть загружен здесь: [Microsoft ODBC Driver 11 for SQL Server — Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Драйвер ODBC для **SUSE Linux Enterprise 11 с пакетом обновления 2 (64-разрядная версия)** требует наличия следующих пакетов и может быть загружен здесь: [Preview 11 драйвера Microsoft ODBC для SQL Server — SUSE Linux](http://go.microsoft.com/fwlink/?LinkId=264916)  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>См. также
[Установка диспетчера драйверов](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)  
