---
title: Установка драйвера OLE DB для SQL Server | Документация Майкрософт
description: Установка и удаление драйвера OLE DB для SQL Server
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
ms.openlocfilehash: 08f33d84ee8c035e1e1d3818e2a036f96af2a280
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989307"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Установка драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Чтобы установить драйвер OLE DB для SQL Server требуется установщик мсоледбскл. msi.
Запустите установщик и сделайте предпочитаемый вариант выбора. Драйвер OLE DB для SQL Server можно установить параллельно с более ранними версиями поставщиков Microsoft OLE DB.

Драйвер OLE DB для SQL Server файлов (мсоледбскл. dll, мсоледбсклр. RLL) устанавливается в `%SYSTEMROOT%\system32\` . Кроме того, x64 мсоледбскл. msi устанавливает 32-разрядные двоичные файлы в `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Все соответствующие параметры реестра для драйвера OLE DB для SQL Server выполняются в рамках процесса установки.  

Драйвер OLE DB для SQL Server файлов заголовков и библиотек (мсоледбскл. h и мсоледбскл. lib) устанавливается в `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`. Кроме того, версия x64 мсоледбскл. msi устанавливает те же файлы `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`в.  

Драйвер OLE DB можно распространять для SQL Server с помощью мсоледбскл. msi. При развертывании приложения может потребоваться установить драйвер OLE DB для SQL Server. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в статьях [Разработка пользовательского пакета начального загрузчика для Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
В x64 мсоледбскл. MSI также устанавливается 32-разрядная версия драйвера OLE DB для SQL Server. Если приложение предназначено для платформы, отличной от той, на которой оно было создано, можно загрузить версии мсоледбскл. msi для x64 и x86.

При вызове msoledbsql.msi по умолчанию устанавливаются только компоненты клиентской части. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью драйвера OLE DB для SQL Server. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Пример:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров /passive, /qn, /qb или /qr программы msiexec необходимо также указать параметр IACCEPTMSOLEDBSQLLICENSETERMS=YES, тем самым явно подтверждая принятие условий соглашения конечного пользователя. Этот параметр указывается только прописными буквами.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Установка драйвера OLE DB для SQL Server в качестве зависимости  
Важно не удалять Драйвер OLE DB для SQL Server, пока не будут удалены все зависимые приложения. Чтобы предоставить пользователям предупреждение о том, что приложение зависит от драйвера OLE DB для SQL Server, используйте параметр установки APPGUID в MSI, как показано ниже.  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.
Параметр APPGUID требует запуска установщика из командной строки с повышенными привилегиями.

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
