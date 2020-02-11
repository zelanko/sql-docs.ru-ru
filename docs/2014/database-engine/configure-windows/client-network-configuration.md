---
title: Конфигурация клиентской сети | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 862c13e61513b46b44ce55df9e66170bbb1ac219
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787121"
---
# <a name="client-network-configuration"></a>Конфигурация клиентской сети
  Клиентское программное обеспечение позволяет клиентским компьютерам подключаться к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в сети. «Клиент» — это клиентская часть приложения, использующая службы, предоставленные сервером, например [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Компьютер, содержащий это приложение, упоминается как *компьютер клиента*.  
  
 В простейшем случае клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может находиться на том же самом компьютере, где находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако обычно клиент подключается к одному или более удаленным серверам через сеть. Архитектура клиент-сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет ему прозрачно управлять множеством клиентов и серверов в сети. Конфигурации клиента по умолчанию достаточно для большинства ситуаций.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Клиенты могут включать приложения различных типов, например:  
  
-   Потребители OLE DB  
  
     Эти приложения подключаются к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик OLE DB является посредником между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениями клиента, которые потребляют данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как набор строк OLE DB. Служебная программа командной строки **sqlcmd** и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]— это примеры приложений OLE DB.  
  
-   Приложения ODBC  
  
     Эти приложения включают клиентские программы, установленные с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], такие как программа командной строки **osql** , а также другие приложения, которые используют драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Клиенты DB-Library  
  
     Эти приложения включают программу командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **** и клиентские программы, записанные в библиотеку DB-Library. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поддержка клиентских приложений, использующих DB-Library, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничена 7,0 компонентами.  
  
> [!NOTE]  
>  Хотя компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] до сих пор поддерживает соединения из существующих приложений, использующих API-интерфейсы DB-Library и Embedded SQL, файлы или документация, необходимые для разработки приложений с использованием этих API, не предоставляются. В следующей версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не будут поддерживаться соединения приложений DB-Library или Embedded SQL. Не используйте DB-Library или Embedded SQL для разработки новых приложений. Удалите все зависимости от DB-Library или Embedded SQL при модификации существующих приложений. Вместо этих API используйте пространство имен SQLClient или такой API, как OLE DB или ODBC. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не включает DB-Library DLL, необходимую для выполнения этих приложений. Для запуска приложений DB-Library или Embedded SQL необходимо иметь доступ к DLL-библиотеке DB-Library для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 или [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 Управление клиентом заключается главным образом в настройке его подключения к компонентам сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]— независимо от типа приложения. В зависимости от требований сайта управление клиентами может варьироваться от небольшого числа операций после ввода имени сервера до построения библиотеки записей пользовательских конфигураций, чтобы обеспечить соответствие в разнообразной среде с несколькими серверами.  
  
 DLL-файл собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит сетевые библиотеки и устанавливается программой установки. Сетевые протоколы не включаются во время установки новых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При обновлении экземпляров включаются предварительно включенные протоколы. Основные сетевые протоколы устанавливаются как часть установки Windows (или через элемент «Сетевые подключения» панели управления). Следующие инструменты используются для управления клиентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager  
  
     И клиент, и компоненты сети сервера управляются с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который объединяет программу сети [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , программу сети клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и диспетчер служб предыдущих версий. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager является оснасткой консоли [!INCLUDE[msCoName](../../includes/msconame-md.md)] управления (MMC). Кроме того, он отображается как узел в оснастке Windows «Управление компьютером». С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отдельные сетевые библиотеки можно включить, отключить, настроить и упорядочить по приоритету.  
  
-   Установка  
  
     Запустите программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и установите сетевые компоненты на компьютере клиента. Отдельные сетевые библиотеки могут быть включены или отключены во время установки, когда установка начата из командной строки.  
  
-   Администратор источников данных ODBC  
  
     С помощью администратора источников данных ODBC можно создавать и изменять источники данных ODBC на компьютерах, работающих под управлением операционной системы Microsoft Windows.  
  
## <a name="in-this-section"></a>в этом разделе  
 [настройка клиентских протоколов](configure-client-protocols.md)  
  
 [Создание или удаление псевдонима сервера, используемого &#40;ом клиента диспетчер конфигурации SQL Server&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
 [Вход в систему SQL Server](logging-in-to-sql-server.md)  
  
 [Открытие администратора источника данных ODBC](open-the-odbc-data-source-administrator.md)  
  
 [Проверьте версию драйвера ODBC SQL Server &#40;Windows&#41;](check-the-odbc-sql-server-driver-version-windows.md)  
  
## <a name="related-content"></a>См. также  
 [Сетевая конфигурация сервера](server-network-configuration.md)  
  
 [Управление службами компонента Database Engine](manage-the-database-engine-services.md)  
  
  
