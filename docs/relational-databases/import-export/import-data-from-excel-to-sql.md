---
title: Импорт данных из Excel в SQL | Документация Майкрософт
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: import-export
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d4bbe4268e60408f5c362c2e68121a4f89b1d82f
ms.sourcegitcommit: 1d81c645dd4fb2f0a6f090711719528995a34583
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2018
ms.locfileid: "37137923"
---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>Импорт данных из Excel в SQL Server или базу данных Azure
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Импортировать данные из файлов Excel в SQL Server или базу данных SQL Azure можно несколькими способами. Некоторые методы позволяют импортировать данные за один шаг непосредственно из файлов Excel. Для других методов необходимо экспортировать данные Excel в виде текста, прежде чем их можно будет импортировать. В этой статье перечислены часто используемые методы и содержатся ссылки для получения дополнительных сведений.

## <a name="list-of-methods"></a>Список методов

-   Вы можете импортировать данные напрямую из Excel в SQL за одно действие, используя одно из следующих средств:
    -   [мастер импорта и экспорта SQL Server](#wiz);
    -   службы [SQL Server Integration Services (SSIS)] (#ssis);
    -   функция [OPENROWSET](#openrowset).
-   Вы можете импортировать данные в два этапа, сначала экспортировав их из Excel в виде текста, а затем импортировав текстовый файл с помощью одного из следующих средств:
    -   [мастер импорта неструктурированных файлов](#import-wiz);
    -   инструкция [BULK INSERT](#bulk-insert);
    -   [BCP](#bcp)
    -   [мастер копирования (Фабрика данных Azure)](#adf-wiz);
    -   [Фабрика данных Azure](#adf).

Если вы хотите импортировать несколько листов из книги Excel, обычно нужно запускать каждое из этих средств отдельно для каждого листа.

Этот список не дает полного описания таких сложных инструментов и служб, как SSIS или фабрика данных Azure. Дополнительные сведения об интересующем вас решении доступны по ссылкам ниже.

> [!IMPORTANT]
> Дополнительные сведения о подключении к файлам Excel, а также об ограничениях и известных проблемах, связанных с загрузкой данных в файлы этого приложения и из них, см. в разделе [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../../integration-services/load-data-to-from-excel-with-ssis.md).

## <a name="wiz"></a> Мастер импорта и экспорта SQL Server

Импортируйте данные напрямую из файлов Excel, выполнив инструкции на страницах мастера импорта и экспорта SQL Server. При необходимости сохраните параметры в виде пакета служб SQL Server Integration Services (SSIS), доступного для настройки и многократного применения в будущем.

Сведения о том, как запустить мастер, см. в разделе [Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

Пример использования мастера для импорта из Excel в SQL Server см. в разделе [Get started with this simple example of the Import and Export Wizard](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md) (Начало работы с помощью простого примера использования мастера импорта и экспорта).

![Подключение к источнику данных Excel](media/excel-connection.png)

## <a name="ssis"></a> Службы SQL Server Integration Services

Если вы работали со службами SSIS и не хотите запускать мастер экспорта и импорта SQL Server, создайте пакет SSIS, который использует для потока данных источник Excel и назначение SQL Server.

Дополнительные сведения о компонентах SSIS см. в указанных ниже статьях.
-   [Источник Excel](../../integration-services/data-flow/excel-source.md)
-   [Назначение SQL Server](../../integration-services/data-flow/sql-server-destination.md)

Чтобы научиться создавать пакеты SSIS, см. руководство [How to Create an ETL Package](../../integration-services/ssis-how-to-create-an-etl-package.md) (Как создать пакет ETL).

![Компоненты потока данных](media/excel-to-sql-data-flow.png)

## <a name="openrowset"></a> OPENROWSET и связанные серверы

> [!NOTE]
> В Azure функции OPENROWSET и OPENDATASOURCE доступны только в управляемом экземпляре базы данных SQL (предварительная версия).

> [!NOTE]
> Поставщик ACE (прежнее название — поставщик Jet), который подключается к источникам данных Excel, предназначен для интерактивного клиентского использования. Если поставщик ACE используется на сервере, особенно в автоматизированных процессах или процессах, выполняющихся параллельно, вы можете получить непредвиденные результаты.

### <a name="distributed-queries"></a>Распределенные запросы

Импортируйте данные напрямую из файлов Excel с помощью функции Transact-SQL `OPENROWSET` или `OPENDATASOURCE`. Такая операция называется *распределенный запрос*.

Перед выполнением распределенного запроса необходимо включить параметр `ad hoc distributed queries` в конфигурации сервера, как показано в примере ниже. Дополнительные сведения см. в статье [ad hoc distributed queries Server Configuration Option](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md) (Параметр конфигурации сервера "ad hoc distributed queries").

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
RECONFIGURE;
GO
```

В приведенном ниже примере кода данные импортируются из листа Excel `Data` в новую таблицу базы данных с помощью `OPENROWSET`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENROWSET('Microsoft.ACE.OLEDB.12.0',
    'Excel 12.0; Database=D:\Desktop\Data.xlsx', [Data$]);
GO
```

Ниже приведен тот же пример с `OPENDATASOURCE`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENDATASOURCE('Microsoft.ACE.OLEDB.12.0',
    'Data Source=D:\Desktop\Data.xlsx;Extended Properties=Excel 12.0')...[Data$];
GO
```

Чтобы *добавить* импортированные данные в *существующую* таблицу, а не создавать новую, используйте синтаксис `INSERT INTO ... SELECT ... FROM ...` вместо синтаксиса `SELECT ... INTO ... FROM ...` из предыдущих примеров.

Для обращения к данным Excel без импорта используйте стандартный синтаксис `SELECT ... FROM ...`.

Дополнительные сведения о распределенных запросах см. в указанных ниже разделах.
-   [Распределенные запросы](https://msdn.microsoft.com/library/ms188721(v=sql.105).aspx). (Распределенные запросы по-прежнему поддерживаются в SQL Server 2016, но документация по этой функции не обновлена.)
-   [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)
-   [OPENDATASOURCE](../../t-sql/functions/openquery-transact-sql.md)

### <a name="linked-servers"></a>Связанные серверы

Кроме того, можно настроить постоянное подключение к файлу Excel как к *связанному серверу*. В примере ниже данные импортируются из листа Excel `Data` на существующем связанном сервере Excel `EXCELLINK` в новую таблицу базы данных с именем `Data_ls`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_ls FROM EXCELLINK...[Data$];
GO
```

Вы можете создать связанный сервер в SQL Server Management Studio или запустить системную хранимую процедуру `sp_addlinkedserver`, как показано в примере ниже.

```sql
DECLARE @RC int

DECLARE @server     nvarchar(128)
DECLARE @srvproduct nvarchar(128)
DECLARE @provider   nvarchar(128)
DECLARE @datasrc    nvarchar(4000)
DECLARE @location   nvarchar(4000)
DECLARE @provstr    nvarchar(4000)
DECLARE @catalog    nvarchar(128)

-- Set parameter values
SET @server =     'EXCELLINK'
SET @srvproduct = 'Excel'
SET @provider =   'Microsoft.ACE.OLEDB.12.0'
SET @datasrc =    'D:\Desktop\Data.xlsx'
SET @provstr =    'Excel 12.0'

EXEC @RC = [master].[dbo].[sp_addlinkedserver] @server, @srvproduct, @provider,
@datasrc, @location, @provstr, @catalog
```

Дополнительные сведения о связанных серверах см. в указанных ниже разделах.
-   [Создание связанных серверов](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)
-   [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)

Примеры и дополнительные сведения о связанных серверах и распределенных запросах см. указанных ниже разделах.
-   [Использование Excel со связанными серверами SQL Server и распределенными запросами](https://support.microsoft.com/help/306397/how-to-use-excel-with-sql-server-linked-servers-and-distributed-queries)
-   [Импорт данных из Excel в SQL Server](https://support.microsoft.com/help/321686/how-to-import-data-from-excel-to-sql-server)

## <a name="prereq"></a> Предварительное требование — сохранение данных Excel как текста
Чтобы использовать другие методы, описанные на этой странице (инструкцию BULK INSERT, средство BCP или фабрику данных Azure), сначала экспортируйте данные Excel в текстовый файл.

В Excel последовательно выберите **Файл | Сохранить как** и выберите как целевой тип файла **Текст (разделитель — табуляция) (\*.txt)** или **CSV (разделитель — запятая) (\*.csv)**.

Если вы хотите экспортировать несколько листов из книги, выполните эту процедуру для каждого листа. Команда **Сохранить как** экспортирует только активный лист.

> [!TIP]
> Чтобы оптимизировать использование средств импорта, сохраняйте листы, которые содержат только заголовки столбцов и строки данных. Если сохраненные данные содержат заголовки страниц, пустые строки, заметки и пр., позже при импорте данных вы можете получить непредвиденные результаты.

## <a name="import-wiz"></a> Мастер импорта неструктурированных файлов

Импортируйте данные, сохраненные как текстовые файлы, выполнив инструкции на страницах мастера импорта неструктурированных файлов.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете импортировать их с помощью мастера импорта неструктурированных файлов.

Дополнительные сведения о мастере импорта неструктурированных файлов см. в разделе [Мастер импорта неструктурированных файлов в SQL](import-flat-file-wizard.md).

## <a name="bulk-insert"></a> Команда BULK INSERT

`BULK INSERT` — это команда Transact-SQL, которую можно выполнить в SQL Server Management Studio. В приведенном ниже примере данные загружаются из файла `Data.csv` с разделителями-запятыми в существующую таблицу базы данных.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать BULK INSERT для их импорта. BULK INSERT не может считывать файлы Excel напрямую.

```sql
USE ImportFromExcel;
GO
BULK INSERT Data_bi FROM 'D:\Desktop\data.csv'
   WITH (
      FIELDTERMINATOR = ',',
      ROWTERMINATOR = '\n'
);
GO
```

Дополнительные сведения см. в указанных ниже разделах.
-   [Массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET(BULK...)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
-   [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)

## <a name="bcp"></a> Средство BCP

BCP — это программа, которая запускается из командной строки. В приведенном ниже примере данные загружаются из файла `Data.csv` с разделителями-запятыми в существующую таблицу базы данных `Data_bcp`.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать BCP для их импорта. BCP не может считывать файлы Excel напрямую.

```sql
bcp.exe ImportFromExcel..Data_bcp in "D:\Desktop\data.csv" -T -c -t ,
```

Дополнительные сведения о программе BCP см. в указанных ниже разделах.
-   [Массовый импорт и экспорт данных с использованием служебной программы BCP (SQL Server)](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
-   [Программа bcp](../../tools/bcp-utility.md)
-   [Подготовка данных к массовому экспорту или импорту](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="adf-wiz"></a> Мастер копирования (Фабрика данных Azure)
Импортируйте данные, сохраненные как текстовые файлы, выполнив инструкции на страницах мастера копирования Фабрики данных Azure.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать фабрику данных Azure для их импорта. Фабрика данных не может считывать файлы Excel напрямую.

Дополнительные сведения о мастере копирования см. в указанных ниже разделах.
-   [Мастер копирования фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
-   [Руководство. Создание конвейера с действием копирования с помощью мастера копирования фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial).

## <a name="adf"></a> Фабрика данных Azure
Если вы уже работали с фабрикой данных Azure и не хотите запускать мастер копирования, создайте конвейер с действием копирования из текстового файла в SQL Server или Базу данных SQL Azure.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать фабрику данных Azure для их импорта. Фабрика данных не может считывать файлы Excel напрямую.

Дополнительные сведения об использовании этих источников и приемников фабрики данных см. в указанных ниже разделах.
-   [Файловая система](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
-   [SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
-   [База данных SQL Azure](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

Чтобы научиться копировать данные с помощью фабрики данных Azure, см. указанные ниже разделы.
-   [Перемещение данных с помощью действия копирования](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
-   [Руководство. Копирование данных из хранилища BLOB-объектов Azure в базу данных SQL с помощью фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database)

## <a name="see-also"></a>См. также:
[Импорт данных из Excel или экспорт данных в Excel с помощью служб SQL Server Integration Services (SSIS)](../../integration-services/load-data-to-from-excel-with-ssis.md)
