---
title: Установка
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: markingmyname
ms.author: maghan
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77d5bcf0d1000b0ceee182ba043f81b4c1221ae8
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388226"
---
# <a name="installing-sql-server-native-client"></a>Установка собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 устанавливается при установке [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]. 
 
 Нет никакого родного клиента сервера S'L Server 2016. Дополнительные сведения см. в разделе [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md). 
 
Также можно извлечь файл sqlncli.msi с веб-страницы пакета дополнительных компонентов SQL Server 2012. Чтобы загрузить самую недавнюю версию родного клиента сервера S'L, перейдите на [® Microsoft S'L Server® 2012 Пакет функций.](https://www.microsoft.com/download/confirmation.aspx?id=29065) Если предыдущая [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версия Native Client раньше, чем S'L Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012, также установлена на компьютере, Native Client 11.0 будет установлена бок о бок с более ранней версией.  
  
 Файлы собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli11.dll, sqlnclir11.rll и s11ch_sqlncli.chm) устанавливаются в следующий каталог.  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Все необходимые настройки реестра для поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняются в процессе установки.  
  
 Заголовочный файл и библиотека собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli.h и sqlncli11.lib) устанавливаются в следующий каталог.  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Помимо установки Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в рамках установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеется распространяемый установщик sqlncli.msi, который можно найти на установочном диске [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в следующем каталоге: `%CD%\Setup\`.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно распространять в виде файла sqlncli.msi. При развертывании приложения может потребоваться установка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в статьях [Разработка пользовательского пакета начального загрузчика для Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Версии файла sqlncli.msi для архитектур x64 и Itanium устанавливают и 64-разрядную версию, и 32-разрядную версию собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если приложение планируется использовать на платформе, отличной от той, на которой оно разрабатывалось, можно скачать из центра загрузки Майкрософт версии sqlncli.msi for x64, Itanium и x86.  
  
 При инициировании sqlncli.msi по умолчанию устанавливаются только компоненты клиентской части. Компоненты клиента — это файлы, поддерживающие работу приложения, разработанного с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Пример:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров /passive, /qn, /qb или /qr программы msiexec необходимо также указать параметр IACCEPTSQLNCLILICENSETERMS=YES, тем самым явно подтверждая принятие условий соглашения конечного пользователя. Этот параметр указывается только прописными буквами.  
  
## <a name="uninstalling-sql-server-native-client"></a>Удаление SQL Server Native Client  
 Поскольку такие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложения, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сервер и инструменты зависят [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] от родного клиента, важно не удалять Native Client до тех пор, пока все зависимые приложения не будут не установлены. Для провайдера пользователей с предупреждением о том, что ваше приложение зависит от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] родного клиента, используйте опцию установки APPGUID в вашем MSI следующим образом:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью родного клиента сервера S'L](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Инструкции по установке](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
