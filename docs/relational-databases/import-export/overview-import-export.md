---
title: "Импорт и экспорт данных в SQL Server и базе данных SQL Azure | Microsoft Docs"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 3c41be0642b13b63367c5601b716b506808472e7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/14/2017

---
# <a name="import-and-export-data-from-sql-server-and-azure-sql-database"></a>Импорт и экспорт данных в SQL Server и базе данных SQL Azure
Для импорта и экспорта данных в SQL Server и базе данных SQL Azure доступны разнообразные методы. Сюда входят инструкции Transact-SQL, программы командной строки и мастеры.

Кроме того, вы можете импортировать и экспортировать данные в разных форматах. Эти форматы включают неструктурированные файлы, файлы Excel, основные типы реляционных баз данных и форматы различных облачных служб.

## <a name="methods-for-importing-and-exporting-data"></a>Методы импорта и экспорта данных

### <a name="use-transact-sql-statements"></a>Использование инструкций Transact-SQL
Вы можете импортировать данные с помощью команд `BULK INSERT` или `OPENROWSET(BULK...)`. Обычно эти команды выполняются в SQL Server Management Studio (SSMS). Дополнительные сведения см. в разделе [Массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET(BULK...)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

### <a name="use-bcp-from-the-command-prompt"></a>Используйте BCP в командной строке
Вы можете импортировать и экспортировать данные с помощью служебной программы командной строки BCP. Дополнительные сведения см. в разделе [Массовый импорт и экспорт данных с использованием программы BCP](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

### <a name="use-the-sql-server-import-and-export-wizard"></a>Использование мастера импорта и экспорта SQL Server
Мастер импорта и экспорта SQL Server позволяет вам экспортировать данные из самых разных источников и импортировать их во множество различных назначений. Чтобы использовать мастер, необходимо установить SQL Server Integration Services (SSIS) или SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

### <a name="design-your-own-import-or-export"></a>Разработка собственного импорта и экспорта
Если вы хотите настроить свой собственный вариант импорта данных, воспользуйтесь следующими функциями или службами.
-   SQL Server Integration Services Дополнительные сведения см. в разделе [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).
-   Фабрика данных Azure Дополнительные сведения см. в разделе [Введение в фабрику данных Azure](https://docs.microsoft.com/azure/data-factory/data-factory-introduction).

## <a name="data-formats-for-import-and-export"></a>Форматы данных для импорта и экспорта

### <a name="supported-formats"></a>Поддерживаемые форматы

Вы можете выполнять импорт и экспорт данных в виде неструктурированных файлов, а также во множестве других форматов, в виде реляционных баз данных и облачных служб. Дополнительные сведения об использовании этих вариантов в конкретных инструментах см. в следующих разделах.
-   Сведения о мастере импорта и экспорта SQL Server см. в разделе [Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md).
-   Сведения о SQL Server Integration Services см. в разделе [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md).
-   Сведения о фабрике данных Azure см. в разделе [Соединители фабрики данных Azure](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-amazon-redshift-connector).

### <a name="commonly-used-data-formats"></a>Часто используемые форматы данных

Для часто используемых форматов данных есть особые возможности и примеры. Дополнительные сведения об этих форматах данных, см. в следующих разделах:
-   сведения об Excel см. в разделе [Импорт из Excel](import-data-from-excel-to-sql.md);
-   сведения о JSON см. в разделе [Импорт документов JSON](../json/import-json-documents-into-sql-server.md);
-   сведения об XML см. в разделе [Импорт и экспорт XML-документов](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md);
-   сведения о хранилище BLOB-объектов Azure см. в разделе [Импорт и экспорт данных из хранилища BLOB-объектов Azure](examples-of-bulk-access-to-data-in-azure-blob-storage.md).

## <a name="next-steps"></a>Следующие шаги
Если вы не знаете, с чего начать импорт или экспорт, попробуйте запустить мастер импорта и экспорта SQL Server. Краткие сведения см. в разделе [Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

