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
manager: craigg
ms.openlocfilehash: 0ad5d49841db9abdd0b512c1d36454eccc5ff73a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782882"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Диспетчер драйверов unixODBC в macOS и Linux поддерживает трассировку входа в вызов ODBC API и выхода драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Для трассировки поведения приложения ODBC, изменить `odbcinst.ini` файла `[ODBC]` раздел для установки значений `Trace=Yes` и `TraceFile` на путь к файлу, который должен содержать трассировки выходные данные; например:

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(Можно также использовать `/dev/stdout` или любое другое устройство для отправки выходных данных существует вместо постоянных файл трассировки.) С указанными выше параметрами каждый раз, приложение загружает диспетчер драйверов unixODBC он будет записывать все вызовы ODBC API, которые она выполнена в выходной файл.

После завершения трассировки приложения удалите `Trace=Yes` из `odbcinst.ini` нужно избежать снижения производительности трассировки и убедитесь, что удалены все файлы трассировки ненужные.
  
Трассировка применяется ко всем приложениям, использующим драйвер в `odbcinst.ini`. Чтобы не выполнять трассировку всех приложений (например, чтобы избежать раскрытия конфиденциальных данных конкретных пользователей), вы можете осуществлять трассировку отдельного экземпляра приложения, предоставив ему расположение частного файла `odbcinst.ini` через переменную среды `ODBCSYSINI`. Пример:  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
В этом случае можно добавить `Trace=Yes` для `[ODBC Driver 13 for SQL Server]` раздел `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Определение файла odbc.ini, используемого драйвером

Драйверы ODBC для Linux и macOS знает, какую `odbc.ini` используется, или путь к `odbc.ini` файл. Тем не менее сведения о том, какие `odbc.ini` файл доступен с помощью средств unixODBC `odbc_config` и `odbcinst`и из документации по диспетчеру драйверов unixODBC.  
  
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

[Документации по unixODBC](http://www.unixodbc.org/doc/UserManual/) описаны различия между пользовательских и системных источников данных. В заключение:  

- Пользовательские имена DSN---это источников данных, которые доступны только для конкретного пользователя. Пользователи могут подключаться с помощью, добавлять, изменять и удалить свои собственные источники данных пользователя. Пользовательские имена DSN хранятся в файле в домашнем каталоге пользователя или его подкаталог.
  
- Системных имен DSN---этих источников данных доступны для каждого пользователя в системе, для подключения, использование их, но можно только добавлены, изменены и удалены системным администратором. Если у пользователя есть DSN пользователя с тем же именем, как системный DSN, пользовательское имя источника данных будет использоваться после подключения этого пользователя.

## <a name="see-also"></a>См. также:
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
