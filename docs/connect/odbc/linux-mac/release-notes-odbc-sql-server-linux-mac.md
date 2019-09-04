---
title: Заметки о выпуске ODBC в Linux и macOS | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: MightyPen
ms.technology: connectivity
ms.topic: conceptual
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: a22cf1c2da261805309c8ac223a8535afbcd34d1
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70152740"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-to-sql-server-on-linux-and-macos"></a>Заметки о выпуске Microsoft ODBC Driver for SQL Server в Linux и macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье перечисляются и описываются новые возможности в версиях [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на платформах Linux и macOS.

<!--
Going forward, please use the new 2-column markdown table for each new H2 version section.
And we are keeping the H2 titles much shorter, partly by removing redundant or obvious info.
We want to track the Month YYYY each new version H2 section is added, at the end of the H2 title.
This is the new standard format for Release Notes article content.

OLD     FILE NAME:    linux-mac/release-notes.md
NOW NEW FILE NAME:    linux-mac/release-notes-odbc-sql-server-linux-mac.md

Thank you.
GeneMi.  2019/04/03.
-->
## <a name="174-august-2019"></a>17.4, август 2019 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Always Encrypted с безопасными анклавами | См. сведения об [использовании функции Always Encrypted с драйвером ODBC](../using-always-encrypted-with-the-odbc-driver.md). |
| Динамическая загрузка OpenSSL | См. [указания по программированию](programming-guidelines.md#bkmk-openssl). |
| Настраиваемые параметры проверки активности TCP. | См. сведения о [подключении к SQL Server](connection-string-keywords-and-data-source-names-dsns.md). |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="173-february-2019"></a>Версия 17.3, февраль 2019 г.

| Изменения | Сведения |
| :------- | :------ |
| Поддерживаются новые дистрибутивы. | &bull; &nbsp; &nbsp; SuSE 15<br/>&bull; &nbsp; &nbsp; Ubuntu 18.10<br/>&bull; &nbsp; &nbsp; macOS 10.14 |
| Режим проверки подлинности Управляемого удостоверения службы Azure Active Directory (назначаемого системой и пользователем). | См. статью [Использование Azure Active Directory с драйвером ODBC](../using-azure-active-directory.md). |
| Возможность передавать входные параметры в потоковом режиме для столбцов Always Encrypted. | Дополнительные сведения см. в разделе [Ограничения драйвера ODBC при использовании Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted). |
| Распределенные транзакции XA. | См. статью [Использование транзакций XA](../use-xa-with-dtc.md).<br/><br/>XA — это сокращение от _eXtended Architecture_ (расширенная архитектура). Так называется стандарт выполнения глобальных транзакций, которые обращаются к нескольким системам хранения данных на стороне сервера. |
| &nbsp; | &nbsp; |

## <a name="172-july-2018"></a>Версия 17.2, июль 2018 г.

| Изменения | Сведения |
| :------- | :------ |
| Поддерживаются новые дистрибутивы. | &bull; &nbsp; &nbsp; Ubuntu 18.04 |
| Классификация данных для Базы данных SQL Azure и SQL Server. | См. статью [Классификация данных](../data-classification.md). |
| Поддержка кодировки UTF-8 на сервере. | &nbsp; |
| `SQLBrowseConnect` | &nbsp; |
| Динамическая зависимость от `libcurl`. | Начиная с этой версии пакет `libcurl` не является явной зависимостью.<br/>Пакет `libcurl` для OpenSSL или NSS требуется при использовании Azure Key Vault или проверки подлинности Azure Active Directory.<br/>Если возникает связанная с пакетом `libcurl` ошибка, убедитесь в том, что он установлен. |
| Обеспечение устойчивости соединения в режиме ожидания с помощью ключевых слов ConnectRetryCount и ConnectRetryInterval в строке подключения. | &bull; &nbsp; &nbsp; Чтобы извлечь количество повторных попыток подключения, используйте атрибут `SQL_COPT_SS_CONNECT_RETRY_COUNT` (только для чтения).<br/><br/>&bull; &nbsp; &nbsp; Чтобы извлечь продолжительность интервала повтора подключения, используйте атрибут `SQL_COPT_SS_CONNECT_RETRY_INTERVAL` (только для чтения).<br/><br/>См. статью [Устойчивость подключения в драйвере ODBC в Windows](../windows/connection-resiliency-in-the-windows-odbc-driver.md). |
| Исправления ошибок. | [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="171-march-2018"></a>Версия 17.1, март 2018 г.

| Изменения | Сведения |
| :------- | :------ |
| Поддержка атрибутов подключения `SQL_COPT_SS_CEKCACHETTL` и `SQL_COPT_SS_TRUSTEDCMKPATHS`. | &bull; &nbsp; &nbsp; `SQL_COPT_SS_CEKCACHETTL` позволяет управлять временем существования локального кэша для ключей шифрования столбцов, а также освобождать его.<br/><br/>&bull; &nbsp; &nbsp; `SQL_COPT_SS_TRUSTEDCMKPATHS` позволяет приложению ограничивать главные ключи столбцов, используемые для операций Always Encrypted, определенным списком.<br/><br/>См. статью [Использование функции Always Encrypted с драйвером ODBC для SQL Server](../using-always-encrypted-with-the-odbc-driver.md). |
| Поддержка загрузки файла `.rll` из расположения по умолчанию. | См. раздел [Загрузка файла ресурсов](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading) в документе об установке. |
| Исправления ошибок. | [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="17"></a>17

**Поддерживаются новые дистрибутивы**: macOS High Sierra и Ubuntu 17.10 

**Повышение производительности**: производительность при выполнении драйвером преобразования из UTF-8 в UTF-16 и обратно увеличена более чем в 10 раз.

**Добавлены возможности**:

Поддержка Always Encrypted для API BCP

Новый атрибут строки подключения UseFMTOnly предписывает драйверу использовать старые метаданные в особых случаях, в которых требуются временные таблицы.

Поддержка Управляемого экземпляра SQL Azure (расширенная закрытая предварительная версия). 
> [!NOTE]
> При использовании Управляемого экземпляра есть ряд особенностей.
> -   FILESTREAM не поддерживается. 
> -   Доступ к локальной файловой системе не поддерживается, однако требуется, например, для файлов трассировки. 
> -   Создание пользовательских типов по локальным путям не поддерживается. 
> -   Встроенная проверка подлинности Windows не поддерживается. 
> -   DTC не поддерживается 
> -   Учетная запись sa отсутствует (учетная запись по умолчанию называется cloudSA).
> -   В ошибке токена TDS (0xAA) возвращается неправильное имя сервера.
> -   Специальные символы в имени базы данных не поддерживаются. 
> -   Инструкция ALTER DATABASE [имя_БД1] MODIFY NAME = [имя_БД2] не поддерживается.
> -   Сообщения об ошибках всегда выводятся на английском языке независимо от выбранного языка (так же как в Azure). 

## <a name="131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos-may-2017"></a>Версия 13.1, для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS, май 2017 г.

В драйвере ODBC 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] добавлена поддержка Always Encrypted и Azure Active Directory при использовании в сочетании с Microsoft SQL Server 2016.

**Поддерживаются новые дистрибутивы**: OS X 10.11 и macOS 10.12 поддерживаются в первой версии драйвера ODBC для macOS. Кроме того, теперь поддерживается Ubuntu 16.10 наравне с Red Hat 6 и 7 и SUSE 12. Для каждой платформы есть соответствующий пакет (RPM или DEB), упрощающий установку и настройку.  Инструкции по установке см. в статье [Установка Microsoft ODBC Driver for SQL Server на Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

**Изменения в поддержке диспетчера пакетов unixODBC 2.3.1**: драйвер ODBC больше не зависит от пользовательских пакетов для диспетчера драйверов unixODBC (исключением является RedHat 6). Вместо этого используется диспетчер пакетов дистрибутива для разрешения зависимости UnixODBC из репозиториев дистрибутива.

**Поддержка API BCP**: драйвер ODBC в Linux и macOS теперь поддерживает использование [функций API BCP (**bcp_init** и других)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md).

## <a name="130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Версия 13.0, для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux

Драйвер Microsoft ODBC Driver 13.0 for SQL Server теперь также поддерживает SQL Server 2014 и SQL Server 2016.  

**Поддерживаются новые дистрибутивы**:

Теперь Ubuntu поддерживается наравне с Red Hat и SUSE. Для каждой платформы есть соответствующий пакет (RPM или DEB), упрощающий установку и настройку.  Инструкции по установке см. в статье [Установка Microsoft ODBC Driver for SQL Server на Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

**Поддержка диспетчера драйверов unixODBC 2.3.1**: помимо обновления диспетчера драйверов, также появился пакет, который упрощает установку и настройку этой зависимости.  

**Разрешение IP-адресов прозрачной сети**: это вариант существующей функции отработки отказа в сети с подсетями, который влияет на последовательность подключения драйвера в случае, когда с именем узла связано несколько IP-адресов, но первый разрешенный IP-адрес не отвечает на запросы.

**Поддержка TLS 1.2**: драйвер Microsoft ODBC Driver 13.0 for SQL Server в Linux теперь поддерживает протокол TLS 1.2 при использовании защищенного обмена данными с SQL Server.

## <a name="11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Версия 11, для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux

Драйвер ODBC в SUSE Linux (предварительная версия) поддерживает 64-разрядную версию SUSE Linux Enterprise 11 с пакетом обновления 2. Дополнительные сведения см. в статье [System Requirements](../../../connect/odbc/linux-mac/system-requirements.md).  

Драйвер ODBC для Linux поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Дополнительные сведения см. в статье [Поддержка высокой доступности и аварийного восстановления в драйвере ODBC для Linux](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Драйвер ODBC для Linux поддерживает подключения к Базе данных SQL Microsoft Azure. Дополнительные сведения см. в статье [Практическое руководство. Подключение к Базе данных Azure SQL с помощью ODBC](https://msdn.microsoft.com/library/hh974312.aspx).  

В `bcp` добавлен параметр `-l` (время ожидания входа). Дополнительные сведения см. в статье [Подключение с помощью **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
