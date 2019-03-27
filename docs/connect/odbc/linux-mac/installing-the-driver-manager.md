---
title: Установка диспетчера драйверов (драйвер ODBC для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78eaf77064fb96c024c548c320ca9feeec10ce02
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "58305812"
---
# <a name="installing-the-driver-manager"></a>Установка диспетчера драйверов
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Эта статья содержит инструкции по установке диспетчера драйверов unixODBC для использования со всеми версиями драйвера Microsoft ODBC для SQL Server в Linux и macOS.  

> [!IMPORTANT]  
> Перед установкой диспетчера драйверов unixODBC удалите с компьютера все установленные пакеты диспетчера драйверов. Установка диспетчера драйверов unixODBC может вызвать сбой существующего диспетчера драйверов.  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-13-131-and-17"></a>Установка диспетчера драйверов для Microsoft ODBC Driver 13, 13.1 и 17
Зависимость диспетчера драйверов разрешается автоматически системой управления пакета при установке Microsoft ODBC Driver 13, 13.1 или 17 for SQL Server в Linux или macOS, следуя инструкциям в [Установка драйвера Microsoft ODBC для SQL Server в Linux или macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Установка диспетчера драйверов для Microsoft ODBC Driver 11 for SQL Server  

(SUSE и только в Red Hat Linux).

**Использование скрипта установки**  
  
> [!IMPORTANT]  
> Эти инструкции ссылаются на `msodbcsql-11.0.2270.0.tar.gz` (файл установки для Red Hat Linux). В случае установке предварительной версии для SUSE Linux файл называется `msodbcsql-11.0.2260.0.tar.gz`.  

Порядок установки диспетчера драйверов:  
  
1.  Убедитесь, что у вас есть корневое разрешение.  
  
2.  Перейдите в каталог, куда программа скачивания драйвера ODBC Driver [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поместила файл с именем `msodbcsql-11.0.2270.0.tar.gz`. Убедитесь в наличии файла \*.TAR.GZ, который соответствует вашей версии Linux. Чтобы извлечь файлы, выполните следующую команду: **tar xvzf msodbcsql-11.0.2270.0.tar.gz**.  

3.  Перейдите в каталог `msodbcsql-11.0.2270.0`, где должен находиться файл `build_dm.sh`. Можно запустить `build_dm.sh` для установки диспетчера драйверов unixODBC.

4.  Чтобы просмотреть список доступных параметров, выполните следующую команду: **./build_dm.sh --help**.  
  
5.  Когда все готово к установке, а ваш компьютер имеет доступ к внешнему сайту по протоколу FTP, выполните следующую команду: **./build_dm.sh**.

Если компьютер не может получить доступ к внешнему сайту по протоколу FTP, получите `unixODBC-2.3.0.tar.gz`. Вы можете получить `unixODBC-2.3.0.tar.gz` из [ http://www.unixodbc.org ](http://www.unixodbc.org/). Щелкните ссылку **Скачать** в левой части страницы, чтобы перейти на страницу скачивания. Щелкните соответствующую ссылку для скачивания unixODBC-2.3.0 (не unixODBC-2.3.1). В этом выпуске [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версия UnixODBC-2.3.1 не поддерживается. Выполните следующую команду, чтобы начать установки диспетчера драйверов unixODBC: **./build_dm.sh --download-url=file://unixODBC-2.3.0.tar.gz**.  

6.  Введите **YES**, чтобы приступить к распаковке файлов. Эта часть процесса может занять около 5 минут.  

7.  После завершения выполнения скрипта следуйте инструкциям на экране, чтобы установить диспетчер драйверов unixODBC

Теперь все готово для установки драйвера. Дополнительные сведения см. в разделе [Установка Microsoft ODBC Driver for SQL Server в Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).  

**Установка вручную**

Если скрипту установки не удалось завершить работу, самостоятельно выполните настройку и сборку подходящего диспетчера драйверов.

1.  Удалите все старые установленные версии unixODBC (например, unixODBC 2.2.11). В Red Hat Enterprise Linux 5 или 6 выполните следующую команду: **yum remove unixODBC**. В SUSE Linux Enterprise **zypper удалить unixODBC**.  
  
2.  Перейдите на сайт [http://www.unixodbc.org](http://www.unixodbc.org/). Щелкните ссылку **Скачать** в левой части страницы, чтобы перейти на страницу скачивания. Щелкните соответствующую ссылку, чтобы сохранить файл unixODBC-2.3.0.tar.gz на компьютере. В этом выпуске [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версия UnixODBC-2.3.1 не поддерживается.  
  
3.  На компьютере Linux выполните команду: **tar xvzf unixODBC-2.3.0.tar.gz**.  
  
4.  Перейдите в каталог unixODBC-2.3.0.  
  
5.  В командной строке выполните команду: **CPPFLAGS = "-DSIZEOF_LONG_INT = 8»**.  
  
6.  В командной строке выполните команду: **export CPPFLAGS**.  
  
7.  В командной строке выполните команду: **"./configure --prefix=/usr --libdir=/usr/lib64 --sysconfdir=/etc --enable-gui=no --enable-drivers=no --enable-iconv --with-iconv-char-enc=UTF8 --with-iconv-ucode-enc=UTF16LE"**.  
  
8.  В командной строке (выполнив вход в корень) выполните команду: **make**.  
  
9. В командной строке (выполнив вход в корень) выполните команду: **make install**.  

Теперь все готово для установки драйвера. Дополнительные сведения см. в разделе [Установка Microsoft ODBC Driver for SQL Server в Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).  
  
## <a name="see-also"></a>См. также:
[Установка Microsoft ODBC Driver for SQL Server в Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)
