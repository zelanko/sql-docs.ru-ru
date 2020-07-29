---
title: Установка драйвера OLE DB для SQL Server | Документация Майкрософт
description: Установка и удаление OLE DB Driver for SQL Server. Чтобы установить OLE DB Driver for SQL Server, требуется установщик msoledbsql.msi
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 1edd1c6e7a118e152fc1f8e85203434347061da5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007067"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Установка драйвера OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Чтобы установить OLE DB Driver for SQL Server, требуется установщик msoledbsql.msi.
Запустите установщик и сделайте предпочитаемый вариант выбора. OLE DB Driver for SQL Server можно установить параллельно с более ранними версиями поставщиков Microsoft OLE DB.

Файлы OLE DB Driver for SQL Server (msoledbsql.dll, msoledbsqlr.rll) устанавливаются в `%SYSTEMROOT%\system32\`. Кроме того, 64-разрядный msoledbsql.msi устанавливает 32-разрядные двоичные файлы в `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Все необходимые настройки реестра для OLE DB Driver for SQL Server вносятся в процессе установки.  

Файлы заголовка и библиотеки OLE DB Driver for SQL Server (msoledbsql.h и msoledbsql.lib) устанавливаются в `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`. Кроме того, 64-разрядный msoledbsql.msi устанавливает такие же файлы в `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`.  

OLE DB Driver for SQL Server можно распространять с помощью msoledbsql.msi. При развертывании приложения может потребоваться установить OLE DB Driver for SQL Server. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в статьях [Разработка пользовательского пакета начального загрузчика для Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
64-разрядный msoledbsql.msi также устанавливает 32-разрядную версию OLE DB Driver for SQL Server. Если приложение планируется использовать на платформе, отличной от той, на которой оно разрабатывалось, можно скачать версии msoledbsql.msi для x64 и x86.

При вызове msoledbsql.msi по умолчанию устанавливаются только компоненты клиентской части. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью драйвера OLE DB для SQL Server. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Пример:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров /passive, /qn, /qb или /qr программы msiexec необходимо также указать параметр IACCEPTMSOLEDBSQLLICENSETERMS=YES, тем самым явно подтверждая принятие условий соглашения конечного пользователя. Этот параметр указывается только прописными буквами.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Установка OLE DB Driver for SQL Server в качестве зависимости  
Важно не удалять OLE DB Driver for SQL Server до удаления всех зависимых приложений. Чтобы предупредить пользователей о том, что ваше приложение зависит от OLE DB Driver for SQL Server, воспользуйтесь параметром установки APPGUID в MSI-файле, как показано ниже.  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.
Опция APPGUID требует запуска программы установки из командной строки.

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
