---
title: Диспетчер подключений SQL Server Compact Edition | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4fd067d6f01c168861a42895c36024cb4c0a9aa5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082794"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Диспетчер соединений SQL Server Compact Edition
  Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact позволяет пакету подключаться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Целевое назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, содержащееся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений для загрузки данных в таблицы базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, используемый службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для соединения с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, доступен только в 32-разрядной версии.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Настройка диспетчера соединений SQL Server Compact Edition  
 При добавлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к пакету диспетчера соединений Compact [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер, который будет решать задачи соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact соединение во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений `Connections` пакета.  
  
 `ConnectionManagerType` Свойства диспетчера соединений присваивается `SQLMOBILE`.  
  
 Диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact можно настроить следующими способами:  
  
-   указать строку соединения, в которой задается расположение базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact;  
  
-   указать пароль для защищенной паролем базы данных;  
  
-   указать сервер, на котором хранится база данных;  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [SQL Server Compact редактор диспетчера соединений Edition &#40;страница "подключения"&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [SQL Server Compact редактор диспетчера соединений Edition &#40;странице "все"&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
