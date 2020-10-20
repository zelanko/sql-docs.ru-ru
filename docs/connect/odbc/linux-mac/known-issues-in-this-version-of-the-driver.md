---
title: Известные проблемы с драйвером ODBC в Linux и macOS
description: Узнайте об известных проблемах с драйвером Microsoft ODBC Driver for SQL Server в Linux и macOS и способах устранения проблем с подключением.
ms.date: 09/01/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af611dcc4ca45ae18d650af6248b0f53ab8bcb0b
ms.sourcegitcommit: 9122251ab8bbd46ea3c699e741d6842c995195fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847304"
---
# <a name="known-issues-for-the-odbc-driver-on-linux-and-macos"></a>Известные проблемы с драйвером ODBC в Linux и macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Эта статья содержит список известных проблем в Microsoft ODBC Driver 13, 13.1 и 17 for SQL Server на платформах Linux и macOS. В ней также представлены шаги по устранению неполадок с подключением.

## <a name="known-issues"></a>Известные проблемы

Дополнительные проблемы будут опубликованы в [блоге о драйверах SQL Server](https://techcommunity.microsoft.com/t5/SQL-Server/bg-p/SQLServer/label-name/SQLServerDrivers).  

- Из-за ограничений системной библиотеки Alpine Linux поддерживает меньше кодировок символов и языковых стандартов. Например, en_US.UTF-8 недоступен. Дополнительные сведения см. в статье [musl libc - functional differences from glibc](https://wiki.musl-libc.org/functional-differences-from-glibc.html) (Функциональные отличия musl libc от glibc).

- В Windows, Linux и macOS символы из кодировки области личных символов (PUA) или символов, определяемых конечными пользователями (EUDC), могут преобразовываться по-разному. Преобразования, выполняемые на сервере в пределах [!INCLUDE[tsql](../../../includes/tsql-md.md)], используют библиотеку функций преобразования Windows. Преобразования в драйвере используют библиотеки функций преобразования Windows, Linux или macOS. Каждая из библиотек может давать разные результаты при выполнении преобразований. Дополнительные сведения см. в статье [End-User-Defined and Private Use Area Characters](/windows/desktop/Intl/end-user-defined-characters) (Символы, определяемые конечными пользователями, и символы области личных символов).

- Если кодировка клиента — UTF-8, диспетчер драйверов не всегда выполняет преобразование из UTF-8 в UTF-16 правильно. В настоящее время повреждение данных происходит, когда один или несколько символов в строке не являются допустимыми символами UTF-8. Символы ASCII сопоставляются правильно. Диспетчер драйверов пытается выполнить такое преобразование при вызове SQLCHAR-версий интерфейса API ODBC (например, SQLDriverConnectA). Диспетчер драйверов не пытается выполнить такое преобразование при вызове SQLWCHAR-версий ODBC API (например, SQLDriverConnectW).  

- Параметр *ColumnSize* функции **SQLBindParameter** указывает на число символов в типе SQL, а *BufferLength* — это число байтов в буфере приложения. Тем не менее, если используется тип данных SQL `varchar(n)` или `char(n)`, приложение связывает параметр как SQL_C_CHAR для типа C или SQL_C_VARCHAR для типа SQL, а клиент использует кодировку UTF-8, может появиться ошибка "Усечение данных строки справа" от драйвера, даже когда значение *ColumnSize* согласовано с размером типа данных на сервере. Эта ошибка возникает по той причине, что в результате преобразования между кодировками символов длина данных может измениться. Например, символ правого апострофа (U+2019) кодируется в CP-1252 как один байт 0x92, а в UTF-8 — как последовательность из трех байтов 0xe2 0x80 0x99.

Например, если используется кодировка UTF-8 и вы указали значение 1 для параметра *BufferLength* и *ColumnSize* в качестве выходного параметра функции **SQLBindParameter**, а затем пытаетесь получить предыдущий символ, хранящийся в столбце `char(1)` на сервере (в кодировке CP-1252), драйвер пытается преобразовать его в трехбайтовую кодировку UTF-8, однако результат не помещается в однобайтовый буфер. Значение *ColumnSize* сравнивается с *BufferLength* в **SQLBindParameter** перед выполнением преобразования между разными кодовыми страницами в клиенте и на сервере. Поскольку *ColumnSize* для 1 меньше, чем *BufferLength* , например, для 3, драйвер выдает ошибку. Чтобы избежать этой ошибки, убедитесь в том, что после преобразования данные поместятся в указанный буфер или столбец. Обратите внимание на то, что для типа `varchar(n)` значение *ColumnSize* не может превышать 8000.

## <a name="troubleshooting-connection-problems"></a><a id="connectivity"></a> Устранение неполадок с подключением  

Если установить подключение к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью драйвера ODBC не удается, следующие сведения помогут вам определить проблему.  
  
Наиболее распространенная проблема подключения связана с наличием двух установленных копий диспетчера драйверов UnixODBC. Поищите libodbc\*.so\*в /usr. Если отображается более одной версии файла, (возможно) установлено несколько диспетчеров драйверов. Приложение может использовать неправильную версию.
  
Включите журнал соединений, добавив в файл `/etc/odbcinst.ini` раздел со следующими элементами:

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Если возникает другой сбой подключения и файл журнала отсутствует, (возможно) на компьютере присутствуют две копии диспетчера драйверов. В противном случае выходные данные журнала должны быть аналогичны следующему:  
  
```
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 17 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
В случае если кодировка символов ASCII отличается от UTF-8, например: 
  
```
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Существует более одного установленного диспетчера драйверов, и приложение использует не тот диспетчер, либо сборка диспетчера драйверов была выполнена неправильно.  
  
Дополнительные сведения об устранении неполадок подключения см. в статьях:  

- [Шаги для устранения неполадок с подключением SQL](/archive/blogs/sql_protocols/steps-to-troubleshoot-sql-connectivity-issues)  
  
- [Устранение проблем с подключением в SQL Server 2005 — часть I](https://techcommunity.microsoft.com/t5/sql-server/sql-server-2005-connectivity-issue-troubleshoot-part-i/ba-p/383034)  
  
- [Устранение проблем с подключением в SQL Server 2008 с помощью кольцевого буфера подключения](https://techcommunity.microsoft.com/t5/sql-server/connectivity-troubleshooting-in-sql-server-2008-with-the/ba-p/383393)  
  
- [Средство устранения неполадок проверки подлинности SQL Server](/archive/blogs/sqlsecurity/sql-server-authentication-troubleshooter)  

## <a name="next-steps"></a>Дальнейшие действия

Инструкции по установке драйвера ODBC см. в следующих статьях.

- [Установка Microsoft ODBC Driver for SQL Server в Linux](installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Установка Microsoft ODBC Driver for SQL Server в macOS](install-microsoft-odbc-driver-sql-server-macos.md)

Дополнительные сведения см. в [рекомендациях по программированию](programming-guidelines.md) и [заметках о выпуске](release-notes-odbc-sql-server-linux-mac.md).
