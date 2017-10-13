---
title: "Массовый импорт и экспорт данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
caps.latest.revision: 61
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 0cd72ac1a99d3a2ccf121b4b659229b2fc6117c0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="bulk-import-and-export-of-data-sql-server"></a>Массовый импорт и экспорт данных (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных (*массовых данных*) из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и импорт массовых данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или несекционированное представление. 
  
-   *Массовый экспорт* означает копирование данных из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных.

-   *Массовый импорт* означает загрузку данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, можно экспортировать данные из приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel в файл данных, а затем выполнить массовый импорт данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
##  <a name="MethodsForBuliIE"></a> Методы массового импорта и экспорта данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и массовый импорт данных в таблицы или несекционированные представления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Доступны следующие основные методы.  
 
  
|Метод|Описание|Импортирует данные|Экспортирует данные|  
|------------|-----------------|------------------|------------------|  
|[bcp, программа](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|Программа командной строки (Bcp.exe), массово экспортирующая и импортирующая данные и создающая файлы форматирования.|Да|Да|  
|[BULK INSERT, инструкция](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , импортирующая данные непосредственно из файла данных в таблицу базы данных или несекционированное представление.|Да|Нет|  
|[Инструкция INSERT ... Инструкция SELECT * FROM OPENROWSET(BULK...)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , использующая поставщик больших наборов строк OPENROWSET для массового импорта данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции OPENROWSET(BULK…), применяющейся для выборки данных в предложение INSERT.|Да|Нет| 
|[мастер импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)|Мастер создает простые пакеты, которые импортируют и экспортируют данные в многочисленных распространенных форматах, включая базы данных, электронные таблицы и текстовые файлы.|Да|Да|  
  
> [!IMPORTANT]
> Значения файлов с разделителями-запятыми (CSV) не поддерживаются операциями массового импорта SQL Server. Но в некоторых случаях CSV-файл можно использовать как файл данных для массового импорта данных в SQL Server. Обратите внимание, что признаком конца поля CSV-файла не обязательно должна быть запятая. Дополнительные сведения см. в разделе [Подготовка данных к массовому экспорту или импорту (SQL Server)](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).

> [!NOTE]
> Для импорта и экспорта файлов с разделителями база данных SQL Azure и хранилище данных SQL Azure поддерживают только служебную программу bcp.
  
##  <a name="FFs"></a> Файлы форматирования  
 Программа [bcp](../../tools/bcp-utility.md), [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [INSERT ... SELECT * FROM OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) поддерживают использование специализированного *файла форматирования*, в котором хранятся сведения о форматировании для каждого поля в файле данных. Файл форматирования также может содержать сведения о соответствующей таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Файл форматирования может быть использован с целью предоставления всех сведений о форматировании, необходимых для массового экспорта данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и массового импорта данных в него.  
  
 Файлы форматирования обеспечивают гибкость при интерпретации данных, существующих в файле данных, в процессе импорта и при форматировании данных в файле данных в процессе экспорта. Эта гибкость исключает необходимость записи специализированного кода для интерпретации данных или изменения формата данных для особых нужд в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или внешних приложениях. Таким образом, например, если экспортируются данные для загрузки в приложение, файлу данных потребуются значения с разделительными-запятыми. Для вставки запятых в качестве признаков конца полей можно использовать файл форматирования.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два вида файлов форматирования: XML-файлы форматирования и файлы форматирования в формате, отличном от XML.  
  
 Программа [bcp](../../tools/bcp-utility.md) — это единственное средство, позволяющее создать файл форматирования. Дополнительные сведения см. в разделе [Создание файла форматирования (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md). Дополнительные сведения об использовании файлов форматирования см. в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server )](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
> [!NOTE]
> В тех случаях, когда файл форматирования не задан во время выполнения операций массового экспорта или импорта, можно переопределить применяемые по умолчанию параметры форматирования в командной строке.

|См. также|
|---|
|[Подготовка данных к массовому экспорту или импорту (SQL Server)](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)|
|[Форматы данных для массового экспорта или импорта (SQL Server)](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование собственного формата для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование символьного формата для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование собственного формата Юникода для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование символьного формата Юникода для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)|
|[Указание форматов данных для совместимости с помощью программы bcp (SQL Server)](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[Указание типа хранилища файлов с помощью программы bcp (SQL Server)](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](../../relational-databases/import-export/specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[Указание длины поля с помощью программы bcp (SQL Server)](../../relational-databases/import-export/specify-field-length-by-using-bcp-sql-server.md)<br />&emsp;&#9679;&emsp;[Определение признаков конца поля и строки (SQL Server)](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)|
|[Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)|
|[Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)|
|[Файлы форматирования для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Создание файла форматирования (SQL Server)](../../relational-databases/import-export/create-a-format-file-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование файла форматирования для пропуска столбца таблицы (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование файла форматирования для пропуска поля данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)<br />&emsp;&#9679;&emsp;[Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)|
 
  
## <a name="more-information"></a>Дополнительные сведения  
 [Предварительные условия для минимального протоколирования массового импорта данных](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Примеры массового импорта и экспорта XML-документов (SQL Server)](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [Копирование баз данных на другие серверы](../../relational-databases/databases/copy-databases-to-other-servers.md)   
 [Выполнение массовой загрузки XML-данных (SQLXML 4.0)](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)   

  
  

