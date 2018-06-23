---
title: Назначение "SQL Server Compact Edition" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 59754dabe5cfb4da9fc131874fb6e04057cee959
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095248"
---
# <a name="sql-server-compact-edition-destination"></a>Назначение «SQL Server Compact Edition»
  Назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact записывает данные в базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, используемый службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для соединения с источниками данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, доступен только в 32-разрядной версии.  
  
 Настройка назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact производится путем указания имени таблицы, в которую назначение SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact вставляет данные. Пользовательское свойство TableName назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact содержит имя таблицы.  
  
 Назначение использует диспетчер соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, чтобы подключиться к источнику данных; диспетчер соединений определяет поставщик OLE DB для использования. Дополнительные сведения см. в разделе [Диспетчер соединений SQL Server Compact Edition](../connection-manager/sql-server-compact-edition-connection-manager.md).  
  
 Назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact содержит пользовательское свойство TableName, которое может быть обновлено выражением свойства после загрузки пакета. Дополнительные сведения см. в разделах [Выражения служб Integration Services (SSIS)](../expressions/integration-services-ssis-expressions.md), [Использование выражений свойств в пакетах](../expressions/use-property-expressions-in-packages.md) и [Пользовательские свойства назначения SQL Server Compact Edition](sql-server-compact-edition-destination-custom-properties.md).  
  
 Назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact имеет один вход и не поддерживает вывод ошибок.  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a>Настройка назначения SQL Server Compact Edition  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Common Properties](../common-properties.md)  
  
-   [Пользовательские свойства назначения «SQL Server»](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Поток данных](data-flow.md)  
  
  