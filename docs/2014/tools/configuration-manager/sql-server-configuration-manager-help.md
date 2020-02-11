---
title: Справка диспетчера конфигурации SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9968f22db053bf12a28e3e491817a2c3ac23008
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68186770"
---
# <a name="sql-server-configuration-manager-help"></a>Справка диспетчера конфигурации SQL Server
  Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы настроить службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сетевые соединения. Для создания и управления объектами базы данных, настройки безопасности и создания запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 В этом разделе содержатся разделы справки F1 диалоговых окон в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] С помощью Configuration Manager нельзя настроить версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующую [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="services"></a>Службы  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager управляет службами, связанными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Большинство этих задач могут быть выполнены при помощи диалогового окна «Службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows», но необходимо отметить, что диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет дополнительные операции с управляемыми им службами, такие как применение правильных разрешений при изменении учетной записи службы. Использование обычного диалогового окна служб Windows для настройки любых служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может привести к неправильной работе службы.  
  
 Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения следующих задач со службами:  
  
-   запуск, прекращение и временная остановка служб;  
  
-   настройка служб на автоматический или ручной запуск, отключение служб или изменение других настроек служб;  
  
-   изменение паролей для учетных записей, используемых службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи флагов трассировки (параметры командной строки);  
  
-   просмотр свойств служб.  
  
## <a name="sql-server-network-configuration"></a>Сетевая конфигурация SQL Server  
 Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения следующих задач, относящихся к службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере:  
  
-   включение или отключение сетевого протокола [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   настройка сетевого протокола [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Краткий учебник о настройке протоколов и подключении к компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]см. в разделе [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
## <a name="sql-server-native-client-configuration"></a>Конфигурация собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Клиенты подключаются к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью сетевой библиотеки собственного клиента. Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для следующих задач, относящихся к клиентским приложениям на этом компьютере:  
  
-   при работе с клиентскими приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере указание порядка протоколов при соединении с экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   настройка клиентских протоколов соединения;  
  
-   при работе с клиентскими приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создание псевдонимов экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]с целью предоставить клиентам возможность подключения при помощи пользовательской строки соединения.  
  
 Дополнительные сведения о каждой из этих задач см. в справке F1 соответствующей задачи.  
  
#### <a name="to-open-sql-server-configuration-manager"></a>Запуск диспетчера конфигурации SQL Server  
  
-   В меню **Пуск** последовательно укажите пункты **Все программы**, **Microsoft SQL Server** (версия), **Средства настройки**и выберите **Диспетчер конфигурации SQL Server**.  
  
## <a name="see-also"></a>См. также:  
 [Службы SQL Server](../../../2014/tools/configuration-manager/sql-server-services.md)   
 [SQL Server конфигурация сети](sql-server-network-configuration.md)   
 [Конфигурация SQL Native Client 11,0](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
