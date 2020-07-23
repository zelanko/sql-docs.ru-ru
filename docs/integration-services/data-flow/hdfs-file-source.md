---
title: Источник "Файл HDFS" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3be6be9e43d6e9e643ea76c4d4a08cd5b370b343
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920287"
---
# <a name="hdfs-file-source"></a>Источник "Файл HDFS"

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Компонент "Источник "Файл HDFS" позволяет пакету служб SSIS считывать данные из файла HDFS. Поддерживаются следующие форматы файлов: TEXT и AVRO. Источники данных ORC не поддерживаются.  
  
 Чтобы настроить источник "Файл HDFS", перетащите источник "Файл HDFS" в конструктор потоков данных и дважды щелкните этот компонент, чтобы открыть редактор.  
  
 ![Редактор источников HDFS-файлов](../../integration-services/data-flow/media/hdfs-file-source.png "Редактор источников HDFS-файлов")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры на вкладке **Общие** в диалоговом окне **Редактор источника "Файл Hadoop"** .  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены HDFS-файлы.|  
|**Путь к файлу**|Укажите имя HDFS-файла.|  
|**Формат файлов**|Укажите формат HDFS-файла. Доступны следующие значения: TEXT и AVRO. Источники данных ORC не поддерживаются.|  
|**Знак-разделитель столбцов**|Если выбран текстовый формат, укажите знак-разделитель столбцов.|  
|**Имена столбцов в первой строке данных**|Если выбран текстовый формат, укажите, будет ли первая строка файла содержать имена столбцов.|  
  
 После настройки этих параметров перейдите на вкладку **Столбцы** , чтобы сопоставить исходные столбцы с целевыми столбцами в потоке данных.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Назначение «Файл HDFS»](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  
