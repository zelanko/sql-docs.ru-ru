---
title: "Справка диспетчера конфигурации SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Диспетчер конфигурации SQL Server, справка"
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Справка диспетчера конфигурации SQL Server
  Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы настроить службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сетевые соединения. Для создания и управления объектами базы данных, настройки безопасности и создания запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 В этом разделе содержатся разделы справки F1 диалоговых окон в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] С помощью диспетчера конфигурации нельзя настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющий версию, предшествующую [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## Службы  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляет службами, относящимися к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Большинство этих задач могут быть выполнены при помощи диалогового окна «Службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows», но необходимо отметить, что диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет дополнительные операции с управляемыми им службами, такие как применение правильных разрешений при изменении учетной записи службы. Использование обычного диалогового окна служб Windows для настройки любых служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может привести к неправильной работе службы.  
  
 Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения следующих задач со службами:  
  
-   запуск, прекращение и временная остановка служб;  
  
-   настройка служб на автоматический или ручной запуск, отключение служб или изменение других настроек служб;  
  
-   изменение паролей для учетных записей, используемых службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи флагов трассировки (параметры командной строки);  
  
-   просмотр свойств служб.  
  
## Сетевая конфигурация SQL Server  
 Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения следующих задач, относящихся к службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере:  
  
-   включение или отключение сетевого протокола [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   настройка сетевого протокола [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Краткий учебник о настройке протоколов и подключении к компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] см. в разделе [Учебник. Приступая к работе с компонентом Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
## Конфигурация собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключаются к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи сетевой библиотеки собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для следующих задач, относящихся к клиентским приложениям на этом компьютере:  
  
-   при работе с клиентскими приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере указание порядка протоколов при соединении с экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   настройка клиентских протоколов соединения;  
  
-   при работе с клиентскими приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создание псевдонимов экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]с целью предоставить клиентам возможность подключения при помощи пользовательской строки соединения.  
  
 Дополнительные сведения о каждой из этих задач см. в справке F1 соответствующей задачи.  
  
#### Запуск диспетчера конфигурации SQL Server  
  
-   В меню **Пуск** укажите **Все программы**, **Microsoft SQL Server** (версия), **Средства настройки** и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
## См. также раздел  
 [Службы SQL Server](../../tools/configuration-manager/sql-server-services.md)   
 [Сетевая конфигурация SQL Server](../../tools/configuration-manager/sql-server-network-configuration.md)   
 [Конфигурация собственного клиента SQL 11.0](../../tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Выбор сетевого протокола](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  