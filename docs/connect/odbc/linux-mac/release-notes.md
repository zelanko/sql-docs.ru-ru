---
title: Заметки о выпуске. Установка Microsoft ODBC Driver for SQL Server на Linux и macOS | Документация Майкрософт
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: d67b8bba1449cce473baa5313762c4933a72e250
ms.sourcegitcommit: 2ab79765e51913f1df6410f0cd56bf2a13221f37
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2019
ms.locfileid: "56955865"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Заметки о выпуске Microsoft ODBC Driver for SQL Server в Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS

**Новый распределение, поддерживаемое**: macOS 15 SuSE, Ubuntu 18.10, 10.14

**Функции, добавленные**:

- Azure Active Directory управляемого удостоверения службы (системы и назначенным пользователем) режим проверки подлинности, Дополнительные сведения см. [с помощью Azure Active Directory с помощью драйвера ODBC](../using-azure-active-directory.md)
- Возможность потоковой передачи входных параметров к всегда зашифрованным столбцам, Дополнительные сведения см. [ограничения драйвера ODBC при использовании Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted)
- XA распределенные транзакции, Дополнительные сведения см. [с помощью транзакций XA](../use-xa-with-dtc.md)

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS

**Новый распределение, поддерживаемое**: Ubuntu 18.04

**Функции, добавленные**:

Классификация данных для базы данных SQL Azure и SQL Server, Дополнительные сведения см. в разделе [классификации данных](../data-classification.md)

Поддерживает кодировку UTF-8 server

SQLBrowseConnect

Динамические зависимость от `libcurl`:
- Начиная с этой версии `libcurl` пакет не с применением явного зависимостью. `libcurl` Пакета для OpenSSL или NSS требуется для проверки подлинности в хранилище ключей Azure или Azure Active Directory. Если вы столкнулись с ошибкой в отношении `libcurl`, установить его.

Простоя устойчивость подключений с ConnectRetryCount и ConnectRetryInterval ключевые слова в строке подключения (Дополнительные сведения см. в разделе [устойчивость подключения в драйвере ODBC Windows](../windows/connection-resiliency-in-the-windows-odbc-driver.md)):
- Используйте `SQL_COPT_SS_CONNECT_RETRY_COUNT`(доступно только для чтения) для получения числа повторных попыток подключения.
- Используйте `SQL_COPT_SS_CONNECT_RETRY_INTERVAL`(доступно только для чтения), чтобы извлечь продолжительность интервала повтора подключения.
- По умолчанию будет повторена подключения один раз.


[Исправления ошибок](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS

**Функции, добавленные**:

Поддержка `SQL_COPT_SS_CEKCACHETTL` и `SQL_COPT_SS_TRUSTEDCMKPATHS` атрибуты соединения (Дополнительные сведения см. в разделе [использование функции Always Encrypted с драйвером ODBC для SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Разрешает управление времени, который существует в локальном кэше ключей шифрования столбцов, а также его очистки
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Позволяет приложению ограничить операции AE только использовать указанный список главных ключей столбцов



Поддержка загрузки `.rll` из расположения по умолчанию (Дополнительные сведения см. в разделе [разделе «Загрузка файла ресурсов» в документе установки](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading))

[Исправления ошибок](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS

**Новый распределение, поддерживаемое**: macOS High Sierra и Ubuntu 17.10 

**Повышение производительности**: больше 10 раз улучшение производительности, когда драйвер выполняет преобразование из UTF-8/16 и.

**Функции, добавленные**:

Поддержка постоянного шифрования для BCP API

Новый атрибут строки подключения UseFMTOnly драйвер использовать устаревшие метаданные в особых случаях, требующих временных таблиц.

Поддержка управляемый экземпляр Azure SQL (расширенная закрытая Предварительная версия). 
> [!NOTE]
> Существует ряд различий, при использовании управляемого экземпляра:
> -   FILESTREAM не поддерживается 
> -   Доступа к локальной файловой системы не поддерживается, но необходимые для таких вещей, как tracefiles 
> -   Создание определяемого пользователем ТИПА из локального пути не поддерживается. 
> -   Встроенная проверка подлинности Windows не поддерживается 
> -   DTC не поддерживается 
> -   Учетная запись «sa» не присутствует (по умолчанию учетная запись называется «cloudSA»)
> -   Ошибка маркера потока табличных данных (0xAA) возвращает неправильное имя сервера
> -   Специальные символы в имени базы данных не поддерживаются. 
> -   MODIFY NAME инструкции ALTER DATABASE [dbname1] = [dbname2] не поддерживается.
> -   Сообщения об ошибках всегда отображаются на английском языке, вне зависимости от языка параметры (то же, как в Azure) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS  

ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] добавлена поддержка Always Encrypted и Azure Active Directory при использовании в сочетании с Microsoft SQL Server 2016.

**Новый распределение, поддерживаемое**: OS X 10.11 и macOS 10.12 поддерживаются в первой версии драйвера ODBC в macOS. Ubuntu 16.10 теперь также поддерживается, а также Red Hat 6, 7 и SUSE 12. Каждая платформа имеет соответствующие платформы пакета (RPM или DEB), чтобы упростить установку и настройку.  См. в разделе [установке драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) инструкции по установке.

**Изменения в поддержке диспетчера драйверов 2.3.1 unixODBC**: драйвер ODBC больше не зависит от пользовательских упаковки для диспетчера драйверов unixODBC (за исключением RedHat 6) и вместо этого использует диспетчер пакетов распространения, чтобы устранить зависимость UnixODBC в репозитории дистрибутива.

**Поддержка API BCP**: драйвер ODBC для Linux и macOS теперь поддерживает использование [функции BCP API (**bcp_init**и т. д.)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Новые возможности в Microsoft ODBC Driver 13.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на платформе Linux  
С Microsoft ODBC Driver 13.0 для SQL Server SQL Server 2014 и SQL Server 2016 теперь также поддерживаются.  

**Новый распределение, поддерживаемое**:

Теперь Ubuntu поддерживается наравне с Red Hat и SUSE. Каждая платформа имеет соответствующие платформы пакета (RPM или DEB), чтобы упростить установку и настройку.  См. в разделе [установке драйвера](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) инструкции по установке.

**Поддержка диспетчера драйверов 2.3.1 unixODBC**: в дополнение к новой диспетчера драйверов, имеется также пакета для установки этой зависимости, которое облегчает установку и настройку.  

**Разрешение IP-адресов прозрачной сети**: разрешение IP-адресов прозрачной сети — это версия существующего компонента Многоподсетевой отработки отказа, которая влияет на время подключения драйвера в случае, где первый разрешить IP-адрес имени узла не поддерживает ответ, и существует несколько IP-адресов, связанный с именем узла.

**Поддержка TLS 1.2**: The Microsoft ODBC Driver 13.0 для SQL Server в Linux теперь поддерживает TLS 1.2 при использовании защиты обмена данными с SQL Server.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux  
Драйвер ODBC в SUSE Linux (предварительная версия) поддерживает 64-разрядную версию SUSE Linux Enterprise 11 с пакетом обновления 2. Дополнительные сведения см. в статье [System Requirements](../../../connect/odbc/linux-mac/system-requirements.md).  

Драйвер ODBC для Linux поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Дополнительные сведения см. в разделе [драйвера ODBC в Linux Поддержка высокой доступности и аварийного восстановления](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Драйвер ODBC для Linux поддерживает подключения к Базе данных SQL Microsoft Azure. Дополнительные сведения см. в статье [Практическое руководство. Подключение к Базе данных Azure SQL Windows с помощью ODBC](https://msdn.microsoft.com/library/hh974312.aspx).  

`-l` Был добавлен параметр (время ожидания входа) `bcp`. Дополнительные сведения см. в статье [Подключение с помощью **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
