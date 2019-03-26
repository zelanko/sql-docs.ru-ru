---
title: Диспетчер подключений SQL Server Compact Edition | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sqlmobileconnection.connection.f1
- sql13.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 832270ebf439838a01820f876354e892c3cf3d8c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58273870"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Диспетчер соединений SQL Server Compact Edition
  Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact позволяет пакету подключаться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Целевое назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, содержащееся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений для загрузки данных в таблицы базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, используемый службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для соединения с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, доступен только в 32-разрядной версии.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Настройка диспетчера соединений SQL Server Compact Edition  
 Когда диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact добавляется к пакету, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений для разрешения соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact во время выполнения, задают свойства диспетчера соединений и добавляют его к коллекции **Connections** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **SQLMOBILE**.  
  
 Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact можно настроить следующими способами:  
  
-   указать строку соединения, в которой задается расположение базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact;  
  
-   указать пароль для защищенной паролем базы данных;  
  
-   указать сервер, на котором хранится база данных;  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="sql-server-compact-edition-connection-manager-editor-connection-page"></a>Редактор диспетчера соединений SQL Server Compact Edition (страница «Соединение»)
  Диалоговое окно **SQL Server Compact Edition Connection Manager** (Диспетчер соединений SQL Server Compact Edition) позволяет задать свойства для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о диспетчере соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition см. в разделе [Диспетчер соединений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Требуется ввести имя файла базы данных и его путь**  
 Введите путь и имя файла базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Обзор**  
 Перейдите к нужному файлу базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact с помощью диалогового окна **Выбор базы данных SQL Server Compact Edition** .  
  
 **Требуется ввести пароль доступа к базе данных**  
 Введите пароль для базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
## <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Редактор диспетчера соединений SQL Server Compact Edition (страница «Все»)
  Диалоговое окно **Диспетчер соединений SQL Server Compact Edition** позволяет задать свойства для соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о диспетчере соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition см. в разделе [Диспетчер соединений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Пороговое значение для автосжатия**  
 Укажите в виде процентов допустимый размер свободного пространства в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact перед запуском процесса автосжатия.  
  
 **Укрупнение блокировок по умолчанию**  
 Определите число блокировок базы данных, которые установит база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, прежде чем попытается укрупнить блокировки.  
  
 **Время ожидания блокировок по умолчанию**  
 Укажите время по умолчанию (в миллисекундах) ожидания транзакцией блокировок базы данных.  
  
 **Интервал записи**  
 Определите интервал (в секундах) между записями данных на диск зафиксированными транзакциями.  
  
 **Идентификатор локали**  
 Задайте идентификатор локали (LCID) базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Максимальный размер буфера**  
 Определите максимальный объем памяти (в килобайтах), используемый базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact перед записью данных на диск.  
  
 **Максимальный размер базы данных**  
 Укажите максимальный размер (в мегабайтах) базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Режим**  
 Укажите файловый режим, в котором будет открываться база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Значение этого свойства по умолчанию равно **Чтение и запись**.  
  
 Параметр «Режим» имеет четыре значения, описанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Только для чтения**|Определяет доступ к базе данных только для чтения.|  
|**Чтение и запись**|Назначает разрешения на чтение и запись базы данных.|  
|**Монопольно**|Задает монопольный доступ к базе данных.|  
|**Общий доступ на чтение**|Определяет возможность одновременного чтения базы данных другими пользователями.|  
  
 **Сохранять сведения о безопасности**  
 Определите, будет ли осуществляться возврат сведений о безопасности в виде части строки соединения. Значение по умолчанию этого параметра равно **False**.  
  
 **Каталог временных файлов**  
 Задайте расположение временных файлов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Источник данных**  
 Укажите имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Пароль**  
 Введите пароль для базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
