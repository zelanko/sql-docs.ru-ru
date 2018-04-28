---
title: Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4fadd1ddbcf4004b3a6652975c2495db9007d433
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Трассировка доступа к данным с помощью драйвера ODBC в Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Диспетчер драйверов unixODBC в macOS и Linux поддерживает трассировку входа в вызов ODBC API и выхода драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Чтобы проследить поведение приложения ODBC, изменить `odbcinst.ini` файла `[ODBC]` раздел, чтобы задать значения `Trace=Yes` и `TraceFile` на путь к файлу, который должен содержать выходные данные трассировки например:

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(Можно также использовать `/dev/stdout` или имя устройства для отправки выходных данных существует вместо постоянных файл трассировки.) Указанные выше параметры каждый раз, приложение загружает диспетчер драйверов unixODBC он будет записывать все вызовы ODBC API, которые он выполняется в выходной файл.

После завершения трассировки приложения удалите `Trace=Yes` из `odbcinst.ini` файла, чтобы избежать снижения производительности трассировки и убедитесь, все трассировки ненужные файлы удаляются.
  
Трассировка применяется ко всем приложениям, использующим драйвер в `odbcinst.ini`. Чтобы не выполнять трассировку всех приложений (например, чтобы предотвратить раскрытие конфиденциальных сведений о пользователях), можно выполнять трассировку отдельного экземпляра приложения, предоставив ему расположение закрытого `odbcinst.ini`, с использованием `ODBCSYSINI` переменной среды. Например:  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
В этом случае можно добавить `Trace=Yes` для `[ODBC Driver 13 for SQL Server]` раздел `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Определить, какой файл odbc.ini используется драйвер

Драйверы ODBC для Linux и macOS не узнать, какие `odbc.ini` используется, или путь к `odbc.ini` файла. Тем не менее сведения о том, какие `odbc.ini` файла используйте доступен с помощью средств unixODBC `odbc_config` и `odbcinst`и из документации диспетчера драйверов unixODBC.  
  
Например, следующая команда выдает (помимо прочей информации) расположение системных и пользовательских `odbc.ini` файлы, содержащие, соответственно, системные и пользовательские имена DSN:

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

[Документации по unixODBC](http://www.unixodbc.org/doc/UserManual/) описаны различия между пользователем и системных источников данных. В заключение:  

- Пользовательские имена DSN---это источников данных, которые доступны только для определенного пользователя. Пользователей можно подключиться с помощью, добавления, изменения и удаления собственных источников данных пользователя. Пользовательские имена DSN хранятся в файле в домашний каталог пользователя или его подкаталог.
  
- Системных имен DSN---этих источников данных доступны для каждого пользователя системы для подключения с использованием их, но можно только быть добавлены, изменены и системным администратором. Если у пользователя есть DSN пользователя с тем же именем, как системный DSN, DSN пользователя будет использоваться после подключения этого пользователя.

## <a name="see-also"></a>См. также
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
