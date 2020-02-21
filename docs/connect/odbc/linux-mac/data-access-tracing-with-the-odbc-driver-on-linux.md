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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68008823"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Диспетчер драйверов unixODBC в macOS и Linux поддерживает трассировку записи вызова API ODBC и выход из драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Чтобы отслеживать поведение приложения ODBC, измените раздел `odbcinst.ini`файла`[ODBC]`, чтобы задать значения пути к файлу `Trace=Yes` и `TraceFile`, который должен содержать выходные данные трассировки. Например:

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Вы также можете использовать `/dev/stdout` или любое другое имя устройства для отправки выходных данных трассировки туда вместо постоянного файла.) При использовании указанных выше параметров каждый раз, когда приложение загружает диспетчер драйверов unixODBC, он записывает все вызовы API ODBC, которые он выполнил в выходной файл.

После завершения трассировки приложения удалите `Trace=Yes` из файла `odbcinst.ini`, чтобы избежать снижения производительности трассировки, и убедитесь, что все ненужные файлы трассировки удалены.

Трассировка применяется ко всем приложениям, использующим драйвер в `odbcinst.ini`. Чтобы не выполнять трассировку всех приложений (например, чтобы избежать раскрытия конфиденциальных данных конкретных пользователей), вы можете осуществлять трассировку отдельного экземпляра приложения, предоставив ему расположение частного файла `odbcinst.ini` через переменную среды `ODBCSYSINI`. Пример:

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

В этом случае можно добавить `Trace=Yes` в раздел `[ODBC Driver 13 for SQL Server]` `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Определение файла odbc.ini, используемого драйвером

Драйверы Linux и MacOS ODBC не знают, какой `odbc.ini` используется, или какой путь к файлу `odbc.ini`. Однако сведения об используемом файле `odbc.ini` доступны в средствах unixODBC `odbc_config` и `odbcinst`, а также в документации по диспетчеру драйверов unixODBC.

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

В документации по [unixODBC](http://www.unixodbc.org/doc/UserManual/) объясняются различия между пользовательским и системным DSN. В разделе "Сводка" сделайте следующее.

- Пользовательские DSN — это имена DSN, которые доступны только для конкретного пользователя. Пользователи могут подключаться, добавлять, изменять и удалять собственные пользовательские имена DSN. Пользовательские имена DSN хранятся в файле в домашнем каталоге или в подкаталоге пользователя.

- Системные имена DSN — это имена DSN, доступны для использования каждым пользователем в системе для подключения, но их могут добавлять, изменять и удалять только системные администраторы. Если у пользователя есть пользовательское имя DSN с тем же именем, что и у системного имени DSN, то при соединениях этого пользователя будет использоваться пользовательское имя DSN.

## <a name="see-also"></a>См. также:

- [Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
