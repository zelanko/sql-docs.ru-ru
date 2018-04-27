---
title: Задача файловой системы Hadoop | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadoopfiletask.f1
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b963428b347e86b10f8110b21c95b32f1c10eea0
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="hadoop-file-system-task"></a>Задача файловой системы Hadoop
  С помощью задачи файловой системы Hadoop можно копировать файлы из кластера Hadoop, в него и в нем в пакете служб SSIS.  
  
 Чтобы добавить задачу файловой системы Hadoop, перетащите ее в конструктор. Затем дважды щелкните задачу или щелкните правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **Редактор задач файловой системы** .  
  
 ![Редактор задач файловой системы](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Редактор задач файловой системы")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры в диалоговом окне **Редактор задачи файловой системы Hadoop** .  
  
|Поле|Description|  
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
 [Диспетчер подключений файлов](../../integration-services/connection-manager/file-connection-manager.md)  
  
  
