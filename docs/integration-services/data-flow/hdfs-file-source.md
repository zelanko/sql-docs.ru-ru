---
title: "Источник &quot;Файл HDFS&quot; | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hdfsfilesrc.f1"
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Источник &quot;Файл HDFS&quot;
  Компонент "Источник "Файл HDFS" позволяет пакету служб SSIS считывать данные из файла HDFS. Поддерживаются следующие форматы файлов: TEXT и AVRO. Источники данных ORC не поддерживаются.  
  
 Чтобы настроить источник "Файл HDFS", перетащите источник "Файл HDFS" в конструктор потоков данных и дважды щелкните этот компонент, чтобы открыть редактор.  
  
 ![HDFS File Source Editor](../../integration-services/data-flow/media/hdfs-file-source.png "HDFS File Source Editor")  
  
## Параметры  
 Настройте следующие параметры на вкладке **Общие** в диалоговом окне **Редактор источника "Файл Hadoop"**.  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены HDFS-файлы.|  
|**Путь к файлу**|Укажите имя HDFS-файла.|  
|**Формат файла**|Укажите формат HDFS-файла. Доступны следующие значения: TEXT и AVRO. Источники данных ORC не поддерживаются.|  
|**Знак-разделитель столбцов**|Если выбран текстовый формат, укажите знак-разделитель столбцов.|  
|**Имена столбцов в первой строке данных**|Если выбран текстовый формат, укажите, будет ли первая строка файла содержать имена столбцов.|  
  
 После настройки этих параметров перейдите на вкладку **Столбцы**, чтобы сопоставить исходные столбцы с целевыми столбцами в потоке данных.  
  
## См. также  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Назначение HDFS-файлов](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  