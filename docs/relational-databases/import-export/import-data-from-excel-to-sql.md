---
title: Импорт данных из Excel в SQL | Документация Майкрософт
ms.custom: sqlfreshmay19
ms.date: 09/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 68a5542d36731e260ab4aeb5a0734bea2a983108
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75245273"
---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>Импорт данных из Excel в SQL Server или базу данных Azure

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Импортировать данные из файлов Excel в SQL Server или базу данных SQL Azure можно несколькими способами. Некоторые методы позволяют импортировать данные за один шаг непосредственно из файлов Excel. Для других методов необходимо экспортировать данные Excel в виде текста (CSV-файла), прежде чем их можно будет импортировать. В этой статье перечислены часто используемые методы и содержатся ссылки для получения дополнительных сведений.

## <a name="list-of-methods"></a>Список методов

Для импорта данных из Excel можно использовать следующие средства:

| Сначала экспортировать в текст (SQL Server и база данных SQL) | Непосредственно из Excel (только в локальной среде SQL Server) |
| :------------------------------------------------- |:------------------------------------------------- |
| [Мастер импорта неструктурированных файлов](#import-wiz)             |[мастер импорта и экспорта SQL Server](#wiz)        |
| Инструкция [BULK INSERT](#bulk-insert)              |[Службы SQL Server Integration Services](#ssis)    |
| [BCP](#bcp)                                        |Функция [OPENROWSET](#openrowset) <br>            |
| [Мастер копирования (Фабрика данных Azure)](#adf-wiz)       |                                                   |
| [Фабрика данных Azure](#adf).                         |                                                   |
| &nbsp; | &nbsp; |

Если вы хотите импортировать несколько листов из книги Excel, обычно нужно запускать каждое из этих средств отдельно для каждого листа.

Этот список не дает полного описания таких сложных инструментов и служб, как SSIS или фабрика данных Azure. Дополнительные сведения об интересующем вас решении доступны по ссылкам ниже.

> [!IMPORTANT]
> Дополнительные сведения о подключении к файлам Excel, а также об ограничениях и известных проблемах, связанных с загрузкой данных в файлы этого приложения и из них, см. в разделе [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../../integration-services/load-data-to-from-excel-with-ssis.md).

Если у вас не установлен SQL Server или SQL Server есть, но нет SQL Server Management Studio, см. статью [Скачивание SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="wiz"></a> Мастер импорта и экспорта SQL Server

Импортируйте данные напрямую из файлов Excel, выполнив инструкции на страницах мастера импорта и экспорта SQL Server. При необходимости сохраните параметры в виде пакета служб SQL Server Integration Services (SSIS), доступного для настройки и многократного применения в будущем.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].

2. Разверните узел **Базы данных**.
3. Щелкните базу данных правой кнопкой мыши.
4. Наведите указатель мыши на пункт **Задачи**.
5. Выберите один из следующих параметров:

  - **Импорт данных**
  - **Экспорт данных**

    ![Запуск мастера SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg)

![Подключение к источнику данных Excel](media/excel-connection.png)

Пример использования мастера для импорта из Excel в SQL Server см. в разделе [Get started with this simple example of the Import and Export Wizard](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md) (Начало работы с помощью простого примера использования мастера импорта и экспорта).

Сведения о других способах запустить мастер импорта и экспорта см. в разделе [Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

## <a name="ssis"></a> Службы SQL Server Integration Services

Если вы работали со службами SSIS и не хотите запускать мастер экспорта и импорта SQL Server, создайте пакет SSIS, который использует для потока данных источник Excel и назначение SQL Server.

Дополнительные сведения о компонентах SSIS см. в указанных ниже статьях.

- [Источник Excel](../../integration-services/data-flow/excel-source.md)
- [Назначение SQL Server](../../integration-services/data-flow/sql-server-destination.md)

Чтобы научиться создавать пакеты SSIS, см. руководство [How to Create an ETL Package](../../integration-services/ssis-how-to-create-an-etl-package.md) (Как создать пакет ETL).

![Компоненты потока данных](media/excel-to-sql-data-flow.png)

## <a name="openrowset"></a> OPENROWSET и связанные серверы

> [!IMPORTANT]
> В базе данных SQL Azure невозможно импортировать данные непосредственно из Excel. Сначала необходимо экспортировать данные в текстовый файл (CSV). Примеры см. в разделе [Пример](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

> [!NOTE]
> Поставщик ACE (прежнее название — поставщик Jet), который подключается к источникам данных Excel, предназначен для интерактивного клиентского использования. Если поставщик ACE используется на сервере SQL Server, особенно в автоматизированных процессах или процессах, выполняющихся параллельно, вы можете получить непредвиденные результаты.

### <a name="distributed-queries"></a>Распределенные запросы

Импортируйте данные напрямую из файлов Excel в SQL Server с помощью функции Transact-SQL `OPENROWSET` или `OPENDATASOURCE`. Такая операция называется *распределенный запрос*.

> [!IMPORTANT]
> В базе данных SQL Azure невозможно импортировать данные непосредственно из Excel. Сначала необходимо экспортировать данные в текстовый файл (CSV). Примеры см. в разделе [Пример](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

Перед выполнением распределенного запроса необходимо включить параметр `ad hoc distributed queries` в конфигурации сервера, как показано в примере ниже. Дополнительные сведения см. в статье [ad hoc distributed queries Server Configuration Option](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md) (Параметр конфигурации сервера "ad hoc distributed queries").

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
RECONFIGURE;
GO
```

В приведенном ниже примере кода данные импортируются из листа Excel `OPENROWSET` в новую таблицу базы данных с помощью `Sheet1`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENROWSET('Microsoft.ACE.OLEDB.12.0',
    'Excel 12.0; Database=C:\Temp\Data.xlsx', [Sheet1$]);
GO
```

Ниже приведен тот же пример с `OPENDATASOURCE`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENDATASOURCE('Microsoft.ACE.OLEDB.12.0',
    'Data Source=C:\Temp\Data.xlsx;Extended Properties=Excel 12.0')...[Sheet1$];
GO
```

Чтобы *добавить* импортированные данные в *существующую* таблицу, а не создавать новую, используйте синтаксис `INSERT INTO ... SELECT ... FROM ...` вместо синтаксиса `SELECT ... INTO ... FROM ...` из предыдущих примеров.

Для обращения к данным Excel без импорта используйте стандартный синтаксис `SELECT ... FROM ...`.

Дополнительные сведения о распределенных запросах см. в указанных ниже разделах.

- [Распределенные запросы](https://msdn.microsoft.com/library/ms188721(v=sql.105).aspx) (Распределенные запросы по-прежнему поддерживаются в SQL Server 2016, но документация по этой функции не обновлена.)
- [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)
- [OPENDATASOURCE](../../t-sql/functions/openquery-transact-sql.md)

### <a name="linked-servers"></a>Связанные серверы

Кроме того, можно настроить постоянное подключение от SQL Server к файлу Excel как к *связанному серверу*. В примере ниже данные импортируются из листа Excel `Data` на существующем связанном сервере `EXCELLINK` в новую таблицу базы данных SQL Server с именем `Data_ls`.

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
SET @datasrc =    'C:\Temp\Data.xlsx'
SET @provstr =    'Excel 12.0'

EXEC @RC = [master].[dbo].[sp_addlinkedserver] @server, @srvproduct, @provider,
@datasrc, @location, @provstr, @catalog
```

Дополнительные сведения о связанных серверах см. в указанных ниже разделах.

- [Создание связанных серверов](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)
- [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)

Примеры и дополнительные сведения о связанных серверах и распределенных запросах см. указанных ниже разделах.

- [Использование Excel со связанными серверами SQL Server и распределенными запросами](https://support.microsoft.com/help/306397/how-to-use-excel-with-sql-server-linked-servers-and-distributed-queries)
- [Импорт данных из Excel в SQL Server](https://support.microsoft.com/help/321686/how-to-import-data-from-excel-to-sql-server)

## <a name="prereq"></a> Предварительное требование — сохранение данных Excel как текста

Чтобы использовать другие методы, описанные на этой странице (инструкцию BULK INSERT, средство BCP или фабрику данных Azure), сначала экспортируйте данные Excel в текстовый файл.

В Excel последовательно выберите **Файл | Сохранить как** и выберите как целевой тип файла **Текст (разделитель — табуляция) (\*.txt)** или **CSV (разделитель — запятая) (\*.csv)** .

Если вы хотите экспортировать несколько листов из книги, выполните эту процедуру для каждого листа. Команда **Сохранить как** экспортирует только активный лист.

> [!TIP]
> Чтобы оптимизировать использование средств импорта, сохраняйте листы, которые содержат только заголовки столбцов и строки данных. Если сохраненные данные содержат заголовки страниц, пустые строки, заметки и пр., позже при импорте данных вы можете получить непредвиденные результаты.

## <a name="import-wiz"></a> Мастер импорта неструктурированных файлов

Импортируйте данные, сохраненные как текстовые файлы, выполнив инструкции на страницах мастера импорта неструктурированных файлов.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете импортировать их с помощью мастера импорта неструктурированных файлов.

Дополнительные сведения о мастере импорта неструктурированных файлов см. в разделе [Мастер импорта неструктурированных файлов в SQL](import-flat-file-wizard.md).

## <a name="bulk-insert"></a> Команда BULK INSERT

`BULK INSERT` — это команда Transact-SQL, которую можно выполнить в SQL Server Management Studio. В приведенном ниже примере данные загружаются из файла `Data.csv` с разделителями-запятыми в существующую таблицу базы данных.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать BULK INSERT для их импорта. BULK INSERT не может считывать файлы Excel напрямую. С помощью команды BULK INSERT можно импортировать CSV-файл, который хранится локально или в хранилище BLOB-объектов Azure.

```sql
USE ImportFromExcel;
GO
BULK INSERT Data_bi FROM 'C:\Temp\data.csv'
   WITH (
      FIELDTERMINATOR = ',',
      ROWTERMINATOR = '\n'
);
GO
```

Дополнительные сведения и примеры для SQL Server и базы данных SQL см. в следующих разделах:

- [Массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET(BULK...)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)

## <a name="bcp"></a> Средство BCP

BCP — это программа, которая запускается из командной строки. В приведенном ниже примере данные загружаются из файла `Data.csv` с разделителями-запятыми в существующую таблицу базы данных `Data_bcp`.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать BCP для их импорта. BCP не может считывать файлы Excel напрямую. Используется для импорта в SQL Server или базу данных SQL из текстового файла (CSV), сохраненного в локальном хранилище.

> [!IMPORTANT]
> Для текстового файла (CSV), хранящегося в хранилище BLOB-объектов Azure, используйте BULK INSERT или OPENROWSET. Примеры см. в разделе [Пример](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

```console
bcp.exe ImportFromExcel..Data_bcp in "C:\Temp\data.csv" -T -c -t ,
```

Дополнительные сведения о программе BCP см. в указанных ниже разделах.

- [Массовый импорт и экспорт данных с помощью программы bcp](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
- [Программа bcp](../../tools/bcp-utility.md)
- [Подготовка данных к массовому экспорту или импорту](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="adf-wiz"></a> Мастер копирования (Фабрика данных Azure)

Импортируйте данные, сохраненные как текстовые файлы, выполнив инструкции на страницах мастера копирования Фабрики данных Azure.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать фабрику данных Azure для их импорта. Фабрика данных не может считывать файлы Excel напрямую.

Дополнительные сведения о мастере копирования см. в указанных ниже разделах.

- [Мастер копирования фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
- [Руководство. Создание конвейера с действием копирования с помощью мастера копирования фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial).

## <a name="adf"></a> Фабрика данных Azure

Если вы уже работали с фабрикой данных Azure и не хотите запускать мастер копирования, создайте конвейер с действием копирования из текстового файла в SQL Server или Базу данных SQL Azure.

Как было описано выше в разделе [Предварительное требование](#prereq), необходимо экспортировать данные Excel в виде текста, прежде чем вы сможете использовать фабрику данных Azure для их импорта. Фабрика данных не может считывать файлы Excel напрямую.

Дополнительные сведения об использовании этих источников и приемников фабрики данных см. в указанных ниже разделах.

- [Файловая система](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
- [SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
- [База данных SQL Azure](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

Чтобы научиться копировать данные с помощью фабрики данных Azure, см. указанные ниже разделы.

- [Перемещение данных с помощью действия копирования](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
- [Руководство. Копирование данных из хранилища BLOB-объектов Azure в базу данных SQL с помощью фабрики данных](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database)

## <a name="common-errors"></a>Распространенные ошибки

### <a name="microsoftaceoledb120-has-not-been-registered"></a>"Microsoft.ACE.OLEDB.12.0" не зарегистрирован

Эта ошибка возникает, так как не установлен поставщик OLE DB. Установите его через [Распространяемый пакет ядра СУБД Microsoft Access 2010](https://www.microsoft.com/download/details.aspx?id=13255). Не забудьте установить 64-разрядную версию, если Windows и SQL Server — 64-разрядные.

Полный текст ошибки.

```
Msg 7403, Level 16, State 1, Line 3
The OLE DB provider "Microsoft.ACE.OLEDB.12.0" has not been registered.
```

### <a name="cannot-create-an-instance-of-ole-db-provider-microsoftaceoledb120-for-linked-server-null"></a>Не удалось создать экземпляр поставщика OLE DB "Microsoft.ACE.OLEDB.12.0" для связанного сервера "(null)".

Это означает, что Microsoft OLEDB не был настроен должным образом. Чтобы устранить проблему, выполните приведенный ниже код Transact-SQL.

```sql
EXEC sp_MSset_oledb_prop N'Microsoft.ACE.OLEDB.12.0', N'AllowInProcess', 1
EXEC sp_MSset_oledb_prop N'Microsoft.ACE.OLEDB.12.0', N'DynamicParameters', 1
```

Полный текст ошибки.

```
Msg 7302, Level 16, State 1, Line 3
Cannot create an instance of OLE DB provider "Microsoft.ACE.OLEDB.12.0" for linked server "(null)".
```

### <a name="the-32-bit-ole-db-provider-microsoftaceoledb120-cannot-be-loaded-in-process-on-a-64-bit-sql-server"></a>32-разрядный поставщик OLE DB "Microsoft.ACE.OLEDB.12.0" не может быть загружен в процессе на 64-разрядной версии SQL Server.

Это происходит, когда 32-разрядная версия поставщика OLD DB устанавливается вместе с 64-разрядной версией SQL Server. Чтобы устранить эту проблему, удалите 32-разрядную версию и вместо нее установите 64-разрядную версию поставщика OLE DB.

Полный текст ошибки.

```
Msg 7438, Level 16, State 1, Line 3
The 32-bit OLE DB provider "Microsoft.ACE.OLEDB.12.0" cannot be loaded in-process on a 64-bit SQL Server.
```

### <a name="the-ole-db-provider-microsoftaceoledb120-for-linked-server-null-reported-an-error-the-provider-did-not-give-any-information-about-the-error"></a>Поставщик OLE DB "Microsoft.ACE.OLEDB.12.0" для связанного сервера "(null)" сообщил об ошибке. Поставщик не предоставил данных об ошибке.

### <a name="cannot-initialize-the-data-source-object-of-ole-db-provider-microsoftaceoledb120-for-linked-server-null"></a>Не удалось проинициализировать объект источника данных поставщика OLE DB "Microsoft.ACE.OLEDB.12.0" для связанного сервера "(null)".

Обе эти ошибки обычно указывают на ошибку разрешений между процессом SQL Server и файлом. Убедитесь, что учетная запись, с которой выполняется служба SQL Server, имеет разрешение на полный доступ к файлу. Мы не рекомендуем импортировать файлы с настольного компьютера.

Полный текст ошибки.

```
Msg 7399, Level 16, State 1, Line 3
The OLE DB provider "Microsoft.ACE.OLEDB.12.0" for linked server "(null)" reported an error. The provider did not give any information about the error.
```

```
Msg 7303, Level 16, State 1, Line 3
Cannot initialize the data source object of OLE DB provider "Microsoft.ACE.OLEDB.12.0" for linked server "(null)".
```

## <a name="see-also"></a>См. также:

[Импорт данных из Excel или экспорт данных в Excel с помощью служб SQL Server Integration Services (SSIS)](../../integration-services/load-data-to-from-excel-with-ssis.md)
