---
title: "Источник файлов HDFS | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b7ed3c3789b7c28476719422f600106a73bfebd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="hdfs-file-source"></a>Источник "Файл HDFS"
  Компонент "Источник "Файл HDFS" позволяет пакету служб SSIS считывать данные из файла HDFS. Поддерживаются следующие форматы файлов: TEXT и AVRO. Источники данных ORC не поддерживаются.  
  
 Чтобы настроить источник "Файл HDFS", перетащите источник "Файл HDFS" в конструктор потоков данных и дважды щелкните этот компонент, чтобы открыть редактор.  
  
 ![Редактор источника файла HDFS](../../integration-services/data-flow/media/hdfs-file-source.png "редактор источник файлов HDFS")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры на вкладке **Общие** в диалоговом окне **Редактор источника "Файл Hadoop"** .  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены HDFS-файлы.|  
|**Путь к файлу**|Укажите имя HDFS-файла.|  
|**Формат файла**|Укажите формат HDFS-файла. Доступны следующие значения: TEXT и AVRO. Источники данных ORC не поддерживаются.|  
|**Знак-разделитель столбцов**|Если выбран текстовый формат, укажите знак-разделитель столбцов.|  
|**Имена столбцов в первой строке данных**|Если выбран текстовый формат, укажите, будет ли первая строка файла содержать имена столбцов.|  
  
 После настройки этих параметров перейдите на вкладку **Столбцы** , чтобы сопоставить исходные столбцы с целевыми столбцами в потоке данных.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Назначение файлов HDFS](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  

