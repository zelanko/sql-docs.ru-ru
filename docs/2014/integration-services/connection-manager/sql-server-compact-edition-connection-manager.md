---
title: Диспетчер подключений SQL Server Compact Edition | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 752c825cb34fbf2afe5d2306afbd562a49f74b7f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833149"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Диспетчер соединений SQL Server Compact Edition
  Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact позволяет пакету подключаться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Целевое назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, содержащееся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений для загрузки данных в таблицы базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, используемый службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для соединения с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, доступен только в 32-разрядной версии.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Настройка диспетчера соединений SQL Server Compact Edition  
 При добавлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к пакету диспетчера соединений Compact [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер, который будет решать задачи соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact соединение во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений `Connections` пакета.  
  
 Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `SQLMOBILE`.  
  
 Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact можно настроить следующими способами:  
  
-   указать строку соединения, в которой задается расположение базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact;  
  
-   указать пароль для защищенной паролем базы данных;  
  
-   указать сервер, на котором хранится база данных;  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
