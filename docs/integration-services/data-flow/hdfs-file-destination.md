---
title: Назначение HDFS-файлов | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f18f6b0516ab9ae417251e49f5a3cf24fd2aa997
ms.sourcegitcommit: 1c01af5b02fe185fd60718cc289829426dc86eaa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185010"
---
# <a name="hdfs-file-destination"></a>Назначение HDFS-файлов
  Компонент назначения HDFS-файлов позволяет записывать данные в пакете служб SSIS в HDFS-файл. Поддерживаются следующие форматы файлов: Text, Avro и ORC.  
  
 Чтобы настроить назначение HDFS-файлов, перетащите источник HDFS-файлов в конструктор потоков данных и дважды щелкните компонент, чтобы открыть редактор.  
  
 ![Редактор назначения HDFS-файлов](../../integration-services/data-flow/media/hdfs-file-dest.png "Редактор назначения HDFS-файлов")  
  
## <a name="options"></a>Параметры  
 Настройте следующие параметры на вкладке **Общие** в диалоговом окне **Hadoop File Destination Editor** (Редактор назначения файлов Hadoop).  
  
|Поле|Описание|  
|-----------|-----------------|  
|**Hadoop Connection (Подключение Hadoop)**|Укажите существующий диспетчер подключений Hadoop или создайте новый. Этот диспетчер подключений указывает, где размещены HDFS-файлы.|  
|**Путь к файлу**|Укажите имя HDFS-файла.|  
|**Формат файла**|Укажите формат HDFS-файла. Доступны следующие значения: Text, Avro и ORC.|  
|**Знак-разделитель столбцов**|Если выбран текстовый формат, укажите знак-разделитель столбцов.|  
|**Имена столбцов в первой строке данных**|Если выбран текстовый формат, укажите, будет ли первая строка файла содержать имена столбцов.|  
  
 После настройки этих параметров перейдите на вкладку **Столбцы** , чтобы сопоставить исходные столбцы с целевыми столбцами в потоке данных.  

::: moniker range=">= sql-server-ver15"
## <a name="prerequisite-for-orc-format"></a>Необходимые условие для использования формата ORC

Прежде чем использовать формат файлов ORC, нужно установить среду выполнения Java (JRE) версии 1.7.51 или более поздней для соответствующей платформы.

Поддерживаются среды JRE как Zulu, так и Oracle.
-   [Zulu JRE](https://www.azul.com/downloads/zulu/zulu-windows/)
-   [Oracle JRE](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)

### <a name="set-up-the-zulu-jre"></a>Настройка Zulu JRE

1. Скачайте и извлеките ZIP-пакет установки Zulu OpenJDK.

2.  Запустите `sysdm.cpl` из командной строки.

3. На вкладке **Дополнительно** выберите **Переменные среды**.

4. В разделе **Системные переменные** выберите **Создать**.

5. Введите `JAVA_HOME` в поле **Имя переменной**.

6. Выберите **Обзор каталога**, перейдите к папке установки Zulu OpenJDK и выберите вложенную папку `jre`. Нажмите кнопку "ОК". Значение переменной заполняется автоматически.

7. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Создание системной переменной**.

8. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно "Переменные среды".

### <a name="set-up-the-oracle-jre"></a>Настройка Oracle JRE

1. Скачайте и запустите EXE-установщик Oracle JRE.

1. Следуйте указаниям установщика, чтобы завершить настройку.

::: moniker-end

## <a name="see-also"></a>См. также:  
 [Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Источник "Файл HDFS"](../../integration-services/data-flow/hdfs-file-source.md)  
