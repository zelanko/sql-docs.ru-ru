---
title: Диспетчер подключений к нескольким файлам |  | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 22fe47c60aadc0f5014b7aef2171399f8ea0d22a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101800"
---
# <a name="multiple-files-connection-manager"></a>диспетчер соединений с несколькими файлами
  Диспетчер соединений с несколькими файлами позволяет пакету обращаться к существующим файлам и папкам или создавать файлы и папки во время выполнения.  
  
> [!NOTE]  
>  Встроенные задачи и компоненты потока данных в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не используют диспетчер соединений с несколькими файлами. Однако можно использовать этот диспетчер соединений в задаче «Скрипт» и компоненте скрипта. Дополнительные сведения об использовании диспетчеров соединений в задаче «Скрипт» см. в разделе [Соединение с источниками данных в задаче «Скрипт»](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [подключение к источникам данных в компоненте скрипта] (.. / extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>Использование диспетчера соединений с несколькими файлами  
 Свойство `FileUsageType` диспетчера соединений с несколькими файлами определяет, как используется соединение. Диспетчер соединений с несколькими файлами может создавать файлы и папки, а также использовать существующие файлы и папки.  
  
 В следующей таблице перечислены значения `FileUsageType`.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Диспетчер соединений с несколькими файлами использует существующий файл.|  
|**1**|Диспетчер соединений с несколькими файлами создает файл.|  
|**2**|Диспетчер соединений с несколькими файлами использует существующую папку.|  
|**3**|Диспетчер соединений с несколькими файлами создает папку.|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>Конфигурация диспетчера соединений с несколькими файлами  
 Когда к пакету добавляется диспетчер соединений с несколькими файлами, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который разрешает подключение нескольких файлов во время выполнения, устанавливает свойства подключения нескольких файлов и добавляет соединения с несколькими файлами к коллекции пакета `Connections`.  
  
 `ConnectionManagerType` Диспетчера соединений задано значение `MULTIFILE`.  
  
 Настроить диспетчер соединений с несколькими файлами можно следующими способами.  
  
-   Определите тип использования файлов и папок.  
  
-   Определите файлы и папки.  
  
-   Если используется множество файлов и папок, определите порядок, в котором будут обращаться к файлам и папкам.  
  
 Если диспетчер соединения с несколькими файлами ссылается на множество файлов и папок, пути файлов и папок разделяются символом «|». Свойство `ConnectionString` диспетчера соединений имеет следующий формат:  
  
 \<*путь*>|\<*путь*>  
  
 Также можно определить множество файлов и папок, используя символы-шаблоны. Например, чтобы все текстовые файлы C диска значение ссылки `ConnectionString` свойству можно присвоить значение C:\\*.txt.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Добавление диспетчера соединения файлов диалогового окна пользовательского Интерфейса в справочник](add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  