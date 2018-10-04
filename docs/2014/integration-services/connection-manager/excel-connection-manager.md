---
title: Диспетчер подключений Excel | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aa7bc6280afeb9bce7525afc3eb5eb19c73e4c01
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183914"
---
# <a name="excel-connection-manager"></a>Диспетчер соединений с Excel
  Диспетчер соединений Excel делает доступным соединение пакета с существующим файлом рабочей книги [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Источник Excel и назначение «Excel», [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают используйте диспетчер соединений с Excel.  
  
 Если происходит добавление диспетчера соединений Excel к пакету, служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет разрешен как соединение Excel во время выполнения, задает свойства диспетчера соединений и добавляет диспетчер соединений к коллекции `Connections` пакета.  
  
 `ConnectionManagerType` Свойства диспетчера соединений присваивается `EXCEL`.  
  
> [!NOTE]  
>  Подключить защищенный паролем файл Excel нельзя.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Настройка диспетчера соединений Excel  
 Чтобы настроить диспетчер соединений Excel, выполните следующее:  
  
-   Укажите путь файла рабочей книги Excel.  
  
-   Укажите версию приложения Excel, использовавшуюся при создании файла.  
  
-   Укажите, содержатся ли имена столбцов в первой строке данных выбранного рабочего листа или диапазона.  
  
 Если диспетчер соединений Excel используется источником Excel, имена столбцов содержатся с извлеченными данными. Если он используется назначением Excel, имена столбцов включены в записанные данные.  
  
 Диспетчер соединений Excel использует поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet 4.0, который поддерживает драйвер Excel ISAM (индексно-последовательный метод доступа) для соединения, считывания и записи данных в источники данных Excel. Дополнительные сведения о поведении этого поставщика и драйвера при использовании с источниками Excel и назначениями Excel см. в разделе [источник Excel](../data-flow/excel-source.md) и [назначение «Excel»](../data-flow/excel-destination.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Редактор диспетчера соединений с Excel](../excel-connection-manager-editor.md).  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
 Дополнительные сведения о переходе между файлами в группе файлов Excel см. в разделе [Просмотр файлов и таблиц Excel с помощью контейнера "Цикл по каждому элементу"](../control-flow/foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Просмотр файлов и таблиц Excel с помощью контейнера «цикл по каждому элементу»](../control-flow/foreach-loop-container.md)  
  
-   [Импорт данных из Excel или экспорт данных в Excel с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)
  
  
