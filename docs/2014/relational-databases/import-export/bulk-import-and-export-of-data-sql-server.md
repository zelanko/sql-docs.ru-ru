---
title: Массовый импорт и экспорт данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e90afe2092623fa1dd356e51af5fff7a19e9a2ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012122"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a>Массовый импорт и экспорт данных (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных (*массовых данных*) из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и импорт массовых данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или несекционированное представление. Массовый импорт и массовый экспорт имеют большое значение для эффективной передачи данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и разнородными источниками данных. *Групповое Экспортирование* означает копирование данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в файл данных. *Групповое импортирование* означает загрузку данных из файла данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу. Например, можно экспортировать данные из приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel в файл данных, а затем выполнить массовый импорт данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе:**  
  
-   [Введение в операции массового импорта и массового экспорта](#Intro)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="Intro"></a>Общие сведения о выполнении операций импорта и экспорта  
 В настоящем разделе приведен перечень и дано краткое сравнение различных доступных методов массового импорта и экспорта данных. В разделе также приведены сведения о файлах форматирования.  
  
 **В этом разделе:**  
  
-   [Методы для выполнения операций с массовым импортом и экспортом данных](#MethodsForBuliIE)  
  
-   [Файлы форматирования](#FFs)  
  
###  <a name="MethodsForBuliIE"></a>Методы для выполнения операций с массовым импортом и экспортом данных  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает массовый экспорт данных из таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и массовый импорт данных в таблицы или несекционированные представления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Доступны следующие основные методы.  
  
|Метод|Description|Импортирует данные|Экспортирует данные|  
|------------|-----------------|------------------|------------------|  
|[Программа bcp](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|Программа командной строки (Bcp.exe), массово экспортирующая и импортирующая данные и создающая файлы форматирования.|Да|Да|  
|[BULK INSERT, инструкция](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , импортирующая данные непосредственно из файла данных в таблицу базы данных или несекционированное представление.|Да|нет|  
|[ВСТАВИТЬ... SELECT * FROM OPENROWSET (BULK...), инструкция](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)], использующая поставщик больших наборов строк OPENROWSET для массового импорта данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции OPENROWSET(BULK…), применяемой для выборки данных в предложение INSERT.|Да|нет|  
  
> [!IMPORTANT]  
>  Значения файлов с разделителями-запятыми (CSV) не поддерживаются операциями массового импорта SQL Server. Но в некоторых случаях файл CSV может использоваться как файл данных для массового импорта данных в SQL Server. Обратите внимание, что признаком конца поля CSV-файла не обязательно должна быть запятая. Дополнительные сведения см. в разделе [Подготовка данных к массовому экспорту или импорту (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md).  
  
###  <a name="FFs"></a>Файлы форматирования  
 Программа **bcp** , BULK INSERT и INSERT... SELECT \* FROM OPENROWSET (BULK...) поддерживает использование специализированного *файла форматирования* , в котором хранятся сведения о форматировании для каждого поля в файле данных. Файл форматирования также может содержать сведения о соответствующей таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Файл форматирования может быть использован с целью предоставления всех сведений о форматировании, необходимых для массового экспорта данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и массового импорта данных в него.  
  
 Файлы форматирования обеспечивают гибкость при интерпретации данных, существующих в файле данных, в процессе импорта и при форматировании данных в файле данных в процессе экспорта. Эта гибкость исключает необходимость записи специализированного кода для интерпретации данных или изменения формата данных для особых нужд в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или внешних приложениях. Таким образом, например, если экспортируются данные для загрузки в приложение, файлу данных потребуются значения с разделительными-запятыми. Для вставки запятых в качестве признаков конца полей можно использовать файл форматирования.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два вида файлов форматирования: XML-файлы форматирования и файлы форматирования в формате, отличном от XML.  
  
 Программа **bcp** — это единственное средство, которое может создать файл форматирования. Дополнительные сведения см. в разделе [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md). Дополнительные сведения об использовании файлов форматирования см. в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server )](format-files-for-importing-or-exporting-data-sql-server.md).  
  
> [!NOTE]  
>  В тех случаях, когда файл форматирования не задан во время выполнения операций массового экспорта или импорта, можно переопределить применяемые по умолчанию параметры форматирования в командной строке.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Импорт и экспорт данных с помощью служебной программы bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [Сбор данных BULK с помощью BULK INSERT или OPENROWSET&#40;BULK... &#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [Не заключайте значения идентификаторов при выполнении много&#40;ного импорта данных SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Не заменяйте значения NULL или используйте значение по умолчанию во время &#40;ного импорта SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Подготовка данных к экспорту или импорту &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Использование файла форматирования**  
  
-   [Создайте файл форматирования &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Использование файла форматирования для SQL Server &#40;данных при выполнении операций импорта&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Используйте файл форматирования для преобразования столбцов таблицы в поля файла данных &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Используйте файл форматирования для пропуска поля данных &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Используйте файл форматирования для пропуска столбца таблицы &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Используйте символьный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте символьный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Указание форматов данных для совместимости при использовании программы bcp**  
  
1.  [Укажите признаки конца поля и строки &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Указание длины префикса в файлах данных с помощью программы bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Указание типа файлового хранилища с помощью программы bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования для минимального ведения журнала при выполнении массового импорта](prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Файлы форматирования для импорта или экспорта &#40;данных SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [Примеры выполнения операций импорта и экспорта XML-документов &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [Копирование баз данных на другие серверы](../databases/copy-databases-to-other-servers.md)   
 [Выполнение групповой загрузки данных XML &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [Выполнение операций с массовым копированием](../native-client/features/performing-bulk-copy-operations.md)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Файлы форматирования для импорта или экспорта &#40;данных SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
