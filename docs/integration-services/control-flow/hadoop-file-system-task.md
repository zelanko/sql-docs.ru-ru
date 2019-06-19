---
title: Задача файловой системы Hadoop | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadoopfiletask.f1
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ffb3559a379a8d1f64c76072f262b89d41164533
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727630"
---
# <a name="hadoop-file-system-task"></a>Задача файловой системы Hadoop

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  С помощью задачи файловой системы Hadoop можно копировать файлы из кластера Hadoop, в него и в нем в пакете служб SSIS.  
  
 Чтобы добавить задачу файловой системы Hadoop, перетащите ее в конструктор. Затем дважды щелкните задачу или щелкните правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **Редактор задач файловой системы** .  
  
 ![Редактор задач файловой системы](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Редактор задач файловой системы")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры в диалоговом окне **Редактор задачи файловой системы Hadoop** .  
  
|Поле|Описание|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены конечные файлы.|  
|**Hadoop File Path (Путь к файлу Hadoop)**|Укажите путь к файлу или каталогу HDFS.|  
|**Hadoop File Type (Тип файла Hadoop)**|Укажите, чем является объект файловой системы HDFS — файлом или каталогом.|  
|**Перезаписать назначение**|Укажите, следует ли перезаписать целевой файл, если он уже существует.|  
|**Операция**|Укажите операцию. Доступны следующие операции: **CopyToHDFS**, **CopyFromHDFS**и **CopyWithinHDFS**.|  
|**Local File Connection (Локальное подключение файлов)**|Укажите существующий диспетчер подключения файлов или создайте его. Этот диспетчер подключений указывает, где размещены исходные файлы.|  
|**С рекурсией**|Укажите, следует ли копировать вложенные папки рекурсивно.|  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Диспетчер соединения файлов](../../integration-services/connection-manager/file-connection-manager.md)  
  
  
