---
title: Массовый импорт и экспорт данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bfbd00c0079aec3e9bcfa67560962356be1cad4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227694"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a>Массовый импорт и экспорт данных (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных (*массовых данных*) из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и импорт массовых данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или несекционированное представление. Массовый импорт и массовый экспорт имеют большое значение для эффективной передачи данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и разнородными источниками данных. *Массовый экспорт* означает копирование данных из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных. *Массовый импорт* означает загрузку данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, можно экспортировать данные из приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel в файл данных, а затем выполнить массовый импорт данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе.**  
  
-   [Общие сведения о массовом импорте данных и операции массового экспорта](#Intro)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="Intro"></a> Массовый импорт и экспорт Обзор массовых операций  
 В настоящем разделе приведен перечень и дано краткое сравнение различных доступных методов массового импорта и экспорта данных. В разделе также приведены сведения о файлах форматирования.  
  
 **В этом разделе:**  
  
-   [Методы массового импорта и экспорта данных](#MethodsForBuliIE)  
  
-   [Файлы форматирования](#FFs)  
  
###  <a name="MethodsForBuliIE"></a> Методы массового импорта и экспорта данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и массовый импорт данных в таблицы или несекционированные представления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Доступны следующие основные методы.  
  
|Метод|Описание|Импортирует данные|Экспортирует данные|  
|------------|-----------------|------------------|------------------|  
|[bcp, программа](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|Программа командной строки (Bcp.exe), массово экспортирующая и импортирующая данные и создающая файлы форматирования.|Да|Да|  
|[BULK INSERT, инструкция](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , импортирующая данные непосредственно из файла данных в таблицу базы данных или несекционированное представление.|Да|Нет|  
|[Инструкция INSERT ... Инструкция SELECT * FROM OPENROWSET(BULK...)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , использующая поставщик больших наборов строк OPENROWSET для массового импорта данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции OPENROWSET(BULK…), применяющейся для выборки данных в предложение INSERT.|Да|Нет|  
  
> [!IMPORTANT]  
>  Значения файлов с разделителями-запятыми (CSV) не поддерживаются операциями массового импорта SQL Server. Но в некоторых случаях файл CSV может использоваться как файл данных для массового импорта данных в SQL Server. Обратите внимание, что признаком конца поля CSV-файла не обязательно должна быть запятая. Дополнительные сведения см. в разделе [Подготовка данных к массовому экспорту или импорту (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md).  
  
###  <a name="FFs"></a> Файлы форматирования  
 Программа **bcp**, BULK INSERT и INSERT... Инструкции SELECT \* FROM OPENROWSET(BULK...) поддерживают использование специального файла, который называется *файлом форматирования* и служит для хранения сведений о форматировании для каждого поля в файле данных. Файл форматирования также может содержать сведения о соответствующей таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Файл форматирования может быть использован с целью предоставления всех сведений о форматировании, необходимых для массового экспорта данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и массового импорта данных в него.  
  
 Файлы форматирования обеспечивают гибкость при интерпретации данных, существующих в файле данных, в процессе импорта и при форматировании данных в файле данных в процессе экспорта. Эта гибкость исключает необходимость записи специализированного кода для интерпретации данных или изменения формата данных для особых нужд в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или внешних приложениях. Таким образом, например, если экспортируются данные для загрузки в приложение, файлу данных потребуются значения с разделительными-запятыми. Для вставки запятых в качестве признаков конца полей можно использовать файл форматирования.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два вида файлов форматирования: XML-файлы форматирования и файлы форматирования в формате, отличном от XML.  
  
 Программа **bcp** — это единственное средство, позволяющее создать файл форматирования. Дополнительные сведения см. в разделе [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md). Дополнительные сведения об использовании файлов форматирования см. в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server )](format-files-for-importing-or-exporting-data-sql-server.md).  
  
> [!NOTE]  
>  В тех случаях, когда файл форматирования не задан во время выполнения операций массового экспорта или импорта, можно переопределить применяемые по умолчанию параметры форматирования в командной строке.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Массовый импорт и экспорт данных с помощью программы bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [Массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET&#40;МАССОВОГО... &#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Подготовка данных к массовому экспорту или импорту (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Использование файла форматирования**  
  
-   [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для пропуска столбца таблицы (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Задание форматов данных для совместимости с помощью программы bcp**  
  
1.  [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Указание типа файлового хранилища с помощью программы bcp (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Предварительные условия для минимального протоколирования массового импорта данных](prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)   
 [Примеры массового импорта и экспорта XML-документов (SQL Server)](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [Копирование баз данных на другие серверы](../databases/copy-databases-to-other-servers.md)   
 [Выполнение массовой загрузки XML-данных (SQLXML 4.0)](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [Выполнение операций массового копирования](../native-client/features/performing-bulk-copy-operations.md)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
