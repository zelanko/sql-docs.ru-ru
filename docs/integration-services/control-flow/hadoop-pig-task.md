---
title: "Задача Pig для Hadoop | Microsoft Docs"
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
  - "sql13.ssis.designer.hadooppigtask.f1"
ms.assetid: 90646316-9822-48aa-9900-295a33750780
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Задача Pig для Hadoop
  Задача Pig для Hadoop используется для запуска сценария Pig в кластере Hadoop.  
  
 Чтобы добавить задачу Pig для Hadoop, перетащите ее в конструктор. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **Hadoop Pig Task Editor** (Редактор задач Pig для Hadoop).  
  
 ![Hadoop Pig Task Editor](../../integration-services/control-flow/media/hadoop-pig-task.png "Hadoop Pig Task Editor")  
  
## Параметры  
 В диалоговом окне **Hadoop Pig Task Editor** (Редактор задач Pig для Hadoop) настройте следующие параметры.  
  
|Поле|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер указывает, где размещена служба WebHCat.|  
|**Тип источника**|Укажите тип источника запроса. Доступные значения: **ScriptFile** (Файл сценария) и **DirectInput** (Прямой ввод).|  
|**InlineScript (Встроенный сценарий)**|Если значение параметра **SourceType** (Тип источника) — **DirectInput** (Прямой ввод), укажите сценарий Pig.|  
|**HadoopScriptFilePath (Путь к файлу сценария Hadoop)**|Если значение **SourceType** (Тип источника) — **ScriptFile** (Файл сценария), укажите путь к файлу скрипта в Hadoop.|  
|**TimeoutInMinutes (Время ожидания в минутах)**|Укажите время ожидания в минутах. Задание Hadoop останавливается, если оно не завершилось до истечения времени ожидания. Укажите 0, чтобы запланировать асинхронное выполнение задания Hadoop.|  
  
## См. также  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  