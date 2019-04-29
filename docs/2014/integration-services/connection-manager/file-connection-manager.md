---
title: Диспетчер подключения файлов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cf820e3f5a3f4a2ca9db28510b867c5dbc8f3c4f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833827"
---
# <a name="file-connection-manager"></a>диспетчер соединения файлов
  Диспетчер соединения файлов позволяет пакету ссылаться на существующий файл или папку или создавать файл или папку в процессе выполнения. Например, можно установить ссылку на файл Excel. Некоторые компоненты из служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют данные, хранящиеся в файлах, для выполнения своей работы. Например, задача «Выполнение SQL» может ссылаться на файл, содержащий набор инструкций SQL. Другие компоненты выполняют операции с файлами. Например, задача «Файловая система» может ссылаться на файл для его копирования в другое расположение.  
  
## <a name="usage-types-of-the-file-connection-manager"></a>Типы применения в диспетчере соединения файлов  
 Свойство `FileUsageType` диспетчера соединения файлов определяет, как используется соединение файла. Диспетчер подключения файлов может создать файл или папку, а также использовать уже существующий файл или папку.  
  
 В следующей таблице приводятся значения `FileUsageType`.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`0`|Диспетчер подключения файлов использует существующий файл.|  
|`1`|Диспетчер подключения файлов создает файл.|  
|`2`|Диспетчер соединения файлов использует существующую папку.|  
|`3`|Диспетчер соединения файлов создает папку.|  
  
## <a name="multiple-file-or-folder-connections"></a>Соединения с несколькими файлами или папками  
 Диспетчер соединения файлов может ссылаться только на один файл или папку. Для создания ссылки на несколько файлов или папок используйте диспетчер соединения нескольких файлов вместо диспетчера соединений с файлом. Дополнительные сведения см. в статье [Multiple Files Connection Manager](multiple-files-connection-manager.md).  
  
## <a name="configuration-of-the-file-connection-manager"></a>Настройка диспетчера соединения файлов  
 Когда в пакет добавляется диспетчер подключения файлов, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который в процессе выполнения создает соединение файла, устанавливает свойства подключения файла и добавляет подключения файла в коллекцию `Connections` пакета.  
  
 Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `FILE`.  
  
 Диспетчер соединения файлов можно настроить следующим образом.  
  
-   Определить тип применения.  
  
-   Определить файл или папку.  
  
 Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Файл/папка](../file-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
