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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6a18a12c10e23e44b597ec6dc5bddebf6a5a77db
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275793"
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

## <a name="prerequisite-for-orc-file-format"></a>Необходимое условие для использования формата файла ORC
Для использования формата файла ORC требуется Java.
Архитектура сборки Java (32- или 64-разрядная) должна соответствовать архитектуре используемой среды выполнения SSIS.
Были протестированы следующие сборки Java:

- [Zulu OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Среда выполнения Oracle Java SE 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

### <a name="set-up-zulus-openjdk"></a>Настройка Zulu OpenJDK
1. Скачайте и извлеките ZIP-пакет установки.
2. Запустите `sysdm.cpl` из командной строки.
3. На вкладке **Дополнительно** выберите **Переменные среды**.
4. В разделе **Системные переменные** выберите **Создать**.
5. Введите `JAVA_HOME` в поле **Имя переменной**.
6. Выберите **Обзор каталога**, перейдите к извлеченной папке и выберите вложенную папку `jre`.
   Затем нажмите кнопку **ОК**. **Значение переменной** заполняется автоматически.
7. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Создание системной переменной**.
8. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Переменные среды**.
9. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Свойства системы**.

### <a name="set-up-oracles-java-se-runtime-environment"></a>Настройка среды выполнения Oracle Java SE
1. Скачайте и запустите EXE-установщик.
2. Следуйте указаниям установщика, чтобы завершить настройку.

::: moniker-end

## <a name="see-also"></a>См. также:
[Диспетчер подключений Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
[Источник «Файл HDFS»](../../integration-services/data-flow/hdfs-file-source.md)
