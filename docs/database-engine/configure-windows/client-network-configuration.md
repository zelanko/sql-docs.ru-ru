---
title: Конфигурация клиентской сети | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], connections
- Database Engine [SQL Server], network configurations
- connections [SQL Server], client configuration
- client connections [SQL Server], about client network connections
- client computers [SQL Server]
- client connections [SQL Server]
- network connections [SQL Server], client configuration
ms.assetid: c382eacd-0a0c-40a4-958f-9b774eb2d734
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e332cdecb37cea1612de4c808ec9b04f571c6e19
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="client-network-configuration"></a>Конфигурация клиентской сети
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Программное обеспечение клиента дает возможность клиентским компьютерам подключаться к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по сети. «Клиент» — это клиентская часть приложения, использующая службы, предоставленные сервером, например [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Компьютер, содержащий это приложение, упоминается как *компьютер клиента*.  
  
 В простейшем случае клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может находиться на том же самом компьютере, где находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако обычно клиент подключается к одному или более удаленным серверам через сеть. Архитектура клиент-сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет ему прозрачно управлять множеством клиентов и серверов в сети. Конфигурации клиента по умолчанию достаточно для большинства ситуаций.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут включать приложения различных типов, например:  
  
-   Потребители OLE DB  
  
     Эти приложения подключаются к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик OLE DB является посредником между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениями клиента, которые потребляют данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как набор строк OLE DB. Служебная программа командной строки **sqlcmd** и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]— это примеры приложений OLE DB.  
  
-   Приложения ODBC  
  
     Эти приложения включают клиентские программы, установленные с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], такие как программа командной строки **osql** , а также другие приложения, которые используют драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Клиенты DB-Library  
  
     Эти приложения включают программу командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **isql** command prompt utility and clients written to DB-Library. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support for client applications using DB-Library is limited to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 features.  
  
> [!NOTE]  
>  Хотя компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] до сих пор поддерживает соединения из существующих приложений, использующих API-интерфейсы DB-Library и Embedded SQL, файлы или документация, необходимые для разработки приложений с использованием этих API, не предоставляются. В следующей версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не будут поддерживаться соединения приложений DB-Library или Embedded SQL. Не используйте DB-Library или Embedded SQL для разработки новых приложений. Удалите все зависимости от DB-Library или Embedded SQL при модификации существующих приложений. Вместо этих API используйте пространство имен SQLClient или такой API, как OLE DB или ODBC. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не включает DB-Library DLL, необходимую для выполнения этих приложений. Для запуска приложений DB-Library или Embedded SQL необходимо иметь доступ к DLL-библиотеке DB-Library для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 или [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 Управление клиентом заключается главным образом в настройке его подключения к компонентам сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]— независимо от типа приложения. В зависимости от требований сайта управление клиентами может варьироваться от небольшого числа операций после ввода имени сервера до построения библиотеки записей пользовательских конфигураций, чтобы обеспечить соответствие в разнообразной среде с несколькими серверами.  
  
 DLL-файл собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит сетевые библиотеки и устанавливается программой установки. Сетевые протоколы не включаются во время установки новых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При обновлении экземпляров включаются предварительно включенные протоколы. Основные сетевые протоколы устанавливаются как часть установки Windows (или через элемент «Сетевые подключения» панели управления). Следующие инструменты используются для управления клиентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диспетчер конфигураций  
  
     И клиент, и компоненты сети сервера управляются с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который объединяет программу сети [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , программу сети клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и диспетчер служб предыдущих версий. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Диспетчер конфигурации является оснасткой консоли управления (MMC) [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Кроме того, он отображается как узел в оснастке Windows «Управление компьютером». С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отдельные сетевые библиотеки можно включить, отключить, настроить и упорядочить по приоритету.  
  
-   Программа установки  
  
     Запустите программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и установите сетевые компоненты на компьютере клиента. Отдельные сетевые библиотеки могут быть включены или отключены во время установки, когда установка начата из командной строки.  
  
-   Администратор источников данных ODBC  
  
     С помощью администратора источников данных ODBC можно создавать и изменять источники данных ODBC на компьютерах, работающих под управлением операционной системы Microsoft Windows.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)  
  
 [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
 [Вход в систему SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
 [Открытие администратора источника данных ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
 [Проверка версии драйвера ODBC для SQL Server (Windows)](../../database-engine/configure-windows/check-the-odbc-sql-server-driver-version-windows.md)  
  
## <a name="related-content"></a>См. также  
 [Сетевая конфигурация сервера](../../database-engine/configure-windows/server-network-configuration.md)  
  
 [Управление службами компонента Database Engine](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  
