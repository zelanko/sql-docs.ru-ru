---
title: "Замечания - драйвер Microsoft ODBC для SQL Server в Linux и macOS | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 84bb78e184f1bca9e683aeebf46b178e3a7dd61f
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Заметки о выпуске для Microsoft ODBC Driver for SQL Server для Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] на macOS и Linux  

ODBC Driver 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] добавляет поддержку постоянного шифрования и Azure Active Directory при использовании в сочетании с Microsoft SQL Server 2016.

**Новый распределение, поддерживаемое**: OS X 10.11 и macOS 10.12 поддерживаются в первой версии драйвера ODBC в macOS. Ubuntu 16.10 теперь также поддерживается наравне с Red Hat 6, 7 и SUSE 12. Каждая платформа имеет соответствующие платформы пакета (RPM или DEB), чтобы упростить установку и настройку.  В разделе [установке драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) инструкции по установке.

**Изменения в поддержке диспетчера драйверов 2.3.1 unixODBC**: драйвер ODBC больше не зависит от пользовательские упаковки для диспетчера драйверов unixODBC (за исключением RedHat 6) и вместо этого использует диспетчер пакетов распространения, чтобы устранить зависимость UnixODBC из репозиториев распределения.

**Поддержка API BCP**: драйвер ODBC для Linux и macOS теперь поддерживает использование [функции BCP API (**bcp_init**и т. д.)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Новые возможности Microsoft ODBC Driver 13.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux  
С 13.0 драйвера Microsoft ODBC для SQL Server SQL Server 2014 и SQL Server 2016 теперь также поддерживаются.  

**Новый распределение, поддерживаемое**:

Теперь Ubuntu поддерживается наравне с Red Hat и SUSE. Каждая платформа имеет соответствующие платформы пакета (RPM или DEB), чтобы упростить установку и настройку.  В разделе [установке драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) инструкции по установке.

**Поддержка диспетчера драйверов 2.3.1 unixODBC**: в дополнение к новой диспетчера драйверов, имеется также пакета для установки этой зависимости, которое облегчает установку и настройку.  

**Прозрачный разрешение IP-адресов сети**: прозрачный разрешение IP-адресов сети является компонент отказоустойчивых кластеров с несколькими подсетями, влияет на время подключения драйвера там, где первый разрешить IP-адрес имени узла не поддерживает версии ответ и имеется несколько IP-адресов, связанный с именем узла.

**Поддержка TLS 1.2**: 13.0 драйвера Microsoft ODBC для SQL Server в Linux теперь поддерживает TLS 1.2 при использовании безопасных соединений с SQL Server.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC 11 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux  
Драйвер ODBC в SUSE Linux (предварительная версия) поддерживает 64-разрядную версию SUSE Linux Enterprise 11 с пакетом обновления 2. Дополнительные сведения см. в разделе [требования к системе для](../../../connect/odbc/linux-mac/system-requirements.md).  

Драйвер ODBC для Linux поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Дополнительные сведения см. в разделе [драйвер ODBC для Linux Поддержка высокого уровня доступности и аварийного восстановления](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Драйвер ODBC для Linux поддерживает подключения к Базе данных SQL Microsoft Azure. Дополнительные сведения см. в статье [Практическое руководство. Подключение к Базе данных Azure SQL Windows с помощью ODBC](http://msdn.microsoft.com/library/hh974312.aspx).  

`-l` Будет добавлен параметр (время ожидания входа) `bcp`. Дополнительные сведения см. в разделе [соединение с помощью **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).

