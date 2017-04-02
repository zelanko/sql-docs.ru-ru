---
title: "Задача Hadoop Hive | Microsoft Docs"
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
  - "sql13.ssis.designer.hadoophivetask.f1"
ms.assetid: 10ff37c0-9f3f-442a-889b-c351afbdc74c
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Задача Hadoop Hive
  Задача Hadoop Hive используется для запуска скрипта Hive в кластере Hadoop.  
  
 Чтобы добавить задачу Hadoop Hive, перетащите ее в конструктор. Затем дважды щелкните задачу или щелкните правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **Редактор задачи Hadoop Hive**.  
  
 ![Hadoop Hive Task Editor](../../integration-services/control-flow/media/hadoop-hive-task.png "Hadoop Hive Task Editor")  
  
## Параметры  
 Настройте следующие параметры в диалоговом окне **Редактор задачи Hadoop Hive**.  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещена служба WebHCat.|  
|**Тип источника**|Укажите тип источника запроса. Доступные значения: **ScriptFile** (Файл сценария) и **DirectInput** (Прямой ввод).|  
|**InlineScript (Встроенный сценарий)**|Если значение **SourceType** (Тип источника) — **DirectInput** (Прямой ввод), укажите скрипт hive.|  
|**HadoopScriptFilePath (Путь к файлу сценария Hadoop)**|Если значение **SourceType** (Тип источника) — **ScriptFile** (Файл сценария), укажите путь к файлу скрипта в Hadoop.|  
|**TimeoutInMinutes (Время ожидания в минутах)**|Укажите время ожидания в минутах. Задание Hadoop останавливается, если оно не завершилось до истечения времени ожидания. Укажите 0, чтобы запланировать асинхронное выполнение задания Hadoop.|  
  
## См. также  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  