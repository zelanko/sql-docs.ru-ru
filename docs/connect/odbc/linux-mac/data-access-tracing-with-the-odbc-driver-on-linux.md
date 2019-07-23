---
title: Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fa39cd11f70a661de5c284e56f2ccc0f7a5777f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008823"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Диспетчер драйверов unixODBC в macOS и Linux поддерживает трассировку входа в вызов ODBC API и выход из драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Чтобы отслеживать поведение `odbcinst.ini` ODBC приложения, измените `[ODBC]` раздел файла, чтобы задать значения `Trace=Yes` и `TraceFile` путь к файлу, содержащему выходные данные трассировки, например:

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Вы также можете использовать `/dev/stdout` или любое другое имя устройства для отправки выходных данных трассировки вместо постоянного файла.) При использовании указанных выше параметров каждый раз, когда приложение загружает диспетчер драйверов unixODBC, он записывает все вызовы API ODBC, которые он выполнил в выходном файле.

После завершения трассировки приложения удалите `Trace=Yes` `odbcinst.ini` из файла, чтобы избежать потери производительности при трассировке, и убедитесь, что удалены все ненужные файлы трассировки.

Трассировка применяется ко всем приложениям, использующим драйвер в `odbcinst.ini`. Чтобы не выполнять трассировку всех приложений (например, чтобы избежать раскрытия конфиденциальных данных конкретных пользователей), вы можете осуществлять трассировку отдельного экземпляра приложения, предоставив ему расположение частного файла `odbcinst.ini` через переменную среды `ODBCSYSINI`. Пример:

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

В этом случае можно добавить `Trace=Yes` `[ODBC Driver 13 for SQL Server]` в раздел `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Определение файла odbc.ini, используемого драйвером

Драйверы ODBC `odbc.ini` `odbc.ini` для Linux и macOS не знает, какой из них используется, или путь к файлу. Однако сведения о том, `odbc.ini` какой файл используется, доступны в средствах `odbc_config` unixODBC и `odbcinst`, а также в документации по диспетчеру драйверов unixodbc.

Например, следующая команда выдает (помимо прочей информации) расположение системных и пользовательских файлов `odbc.ini`, которые содержат соответственно системные и пользовательские имена DSN:

```
$ odbcinst -j
unixODBC 2.3.1
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/odbcuser/.odbc.ini`
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```

В [документации unixodbc](http://www.unixodbc.org/doc/UserManual/) объясняются различия между пользовательским и системным именами DSN. В сводке:

- Пользовательские DSN---это имена DSN, которые доступны только для конкретного пользователя. Пользователи могут подключаться с помощью, добавлять, изменять и удалять собственные пользовательские имена DSN. Пользовательские имена DSN хранятся в файле в домашнем каталоге пользователя или в подкаталоге.

- Системные имена DSN---эти имена DSN доступны для каждого пользователя в системе для подключения с помощью, но их можно добавлять, изменять и удалять только системным администраторам. Если у пользователя есть пользовательское имя DSN с тем же именем, что и у системного имени DSN, то пользовательское имя DSN будет использоваться при соединениях этого пользователя.

## <a name="see-also"></a>См. также:

- [Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
