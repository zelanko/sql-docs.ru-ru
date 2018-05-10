---
title: Назначение HDFS-файлов | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: da32e08556806506309c1989e7efc6dd05ae52a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="hdfs-file-destination"></a>Назначение HDFS-файлов
  Компонент назначения HDFS-файлов позволяет записывать данные в пакете служб SSIS в HDFS-файл. Поддерживаются следующие форматы файлов: Text, Avro и ORC.  
  
 Чтобы настроить назначение HDFS-файлов, перетащите источник HDFS-файлов в конструктор потоков данных и дважды щелкните компонент, чтобы открыть редактор.  
  
 ![Редактор назначения HDFS-файлов](../../integration-services/data-flow/media/hdfs-file-dest.png "Редактор назначения HDFS-файлов")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры на вкладке **Общие** в диалоговом окне **Hadoop File Destination Editor** (Редактор назначения файлов Hadoop).  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены HDFS-файлы.|  
|**Путь к файлу**|Укажите имя HDFS-файла.|  
|**Формат файла**|Укажите формат HDFS-файла. Доступны следующие значения: Text, Avro и ORC.|  
|**Знак-разделитель столбцов**|Если выбран текстовый формат, укажите знак-разделитель столбцов.|  
|**Имена столбцов в первой строке данных**|Если выбран текстовый формат, укажите, будет ли первая строка файла содержать имена столбцов.|  
  
 После настройки этих параметров перейдите на вкладку **Столбцы** , чтобы сопоставить исходные столбцы с целевыми столбцами в потоке данных.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Источник «Файл HDFS»](../../integration-services/data-flow/hdfs-file-source.md)  
  
  
