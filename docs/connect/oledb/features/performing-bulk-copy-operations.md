---
title: Выполнение операций массового копирования | Документы Microsoft
description: Выполнение операций массового копирования с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], bulk copy operations
- OLE DB Driver for SQL Server, bulk copy operations
- MSOLEDBSQL, bulk copy operations
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f1c5eaf2edc7be8e97dd1386c8b1db2a83b3946
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="performing-bulk-copy-operations"></a>Выполнение операций массового копирования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Функция массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает передачу больших объемов данных в таблицу или представление [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или из них. Данные можно также передать путем указания инструкции SELECT. Данные можно передавать между [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и файлом данных операционной системы, таким как ASCII-файл. Файлы данных могут иметь различные форматы. Формат определяется для массового копирования в файле форматирования. По желанию данные можно загрузить в переменные программы и передать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью функций и методов массового копирования.  
  
 Образец приложения, демонстрирующий эту функцию, в разделе [массового копирования данных с помощью IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 Приложение обычно использует массовое копирование одним из следующих способов.  
  
-   Массовое копирование из таблицы, представления или результирующего набора инструкции Transact-SQL в файл данных, куда данные помещаются в том же формате, что и в таблице или представлении.  
  
     Такой файл называется файлом данных собственного режима.  
  
-   Массовое копирование из таблицы, представления или результирующего набора инструкции Transact-SQL в файл данных, куда данные помещаются в формате, отличном от формата в таблице или представлении.  
  
     В этом случае создается отдельный файл форматирования, который определяет характеристики (тип данных, позицию, длину, признак конца и т. д.) каждого столбца, когда он помещается в файл данных. Если все столбцы преобразуются в символьный формат, результирующий файл называется файлом данных символьного режима.  
  
-   Массовое копирование из файлов данных в таблицу или представление.  
  
     При необходимости файл форматирования используется для определения макета файла данных.  
  
-   Загрузите данные в переменные программы, а затем выполните импорт данных в таблицу или представление с помощью функций массового копирования для массового копирования по строке за раз.  
  
 Файлы данных, используемые функциями массового копирования, не приходится создавать при помощи другой программы массового копирования. Любая другая система может создать файл данных и файл форматирования в соответствии с определениями массового копирования. Эти файлы можно затем использовать в программе массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для импорта данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Например, можно экспортировать данные из электронной таблицы в файл с разделителями-символами табуляции, построить файл форматирования, описывающий файл с разделителями-символами табуляции, а затем использовать функции массового копирования для быстрого импорта данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Файлы данных, созданные при массовом копировании, можно также импортировать в другие приложения. Например, можно использовать функции массового копирования для экспорта данных из таблицы или представления в файл с разделителями-символами табуляции, который затем можно загрузить в электронную таблицу.  
  
 Программисты, пишущие приложения, использующие функции массового копирования, должны следовать основным правилам для обеспечения хорошей производительности массового копирования. Дополнительные сведения о поддержке операций массового копирования в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в разделе [массового импорта и экспорта данных &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Определяемый пользователем тип данных CLR должен быть привязан как двоичные данные. Даже если файл форматирования указывает SQLCHAR как тип данных для целевого столбца определяемого пользователем типа, программа bcp будет рассматривать данные как двоичные.  
  
 Нельзя использовать инструкцию SET FMTONLY OFF с операциями массового копирования. Ее использование может стать причиной завершения операции массового копирования с ошибкой или получению непредвиденных результатов.  
  
## <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server 
 Драйвер OLE DB для SQL Server реализует два метода для выполнения операций массового копирования с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных. Первый метод предполагает использование [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) интерфейс на основе памяти массовое копирование; и второй предполагает использование [IBCPSession](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md) интерфейс для операций массового копирования.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Использование операций массового копирования, работающих с памятью  
 Драйвер OLE DB для SQL Server реализует **IRowsetFastLoad** интерфейс для предоставления поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] операций на основе памяти массового копирования. **IRowsetFastLoad** интерфейс реализует [IRowsetFastLoad::Commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) и [IRowsetFastLoad::InsertRow](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md) методы.  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Включение сеанса для метода IRowsetFastLoad  
 Потребитель уведомляет драйвер OLE DB для SQL Server о необходимости массового копирования, задав драйвер OLE DB для SQL Server относятся свойство источника данных SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE. Со свойством в источнике данных потребитель создает драйвер OLE DB для SQL Server сеанса. Новый сеанс позволяет потребителю получить доступ к **IRowsetFastLoad** интерфейса.  
  
> [!NOTE]  
>  Если **IDataInitialize** интерфейса используется для инициализации источника данных, то необходимо задать свойство SSPROP_IRowsetFastLoad *rgPropertySets* параметр  **IOpenRowset::OpenRowset** метод; в противном случае вызов **OpenRowset** метод возвращает ошибку E_NOINTERFACE.  
  
 Включение сеанса для массового копирования ограничивает драйвер OLE DB для SQL Server поддержку интерфейсов в сеансе. Сеанс с включенным массовым копированием предоставляет только следующие интерфейсы:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Чтобы отключить создание наборы строк для массового копирования включена и вызвать драйвер OLE DB для SQL Server сеанса вернуться к обычной обработке, ssprop_enablefastload значение VARIANT_FALSE.  
  
#### <a name="irowsetfastload-rowsets"></a>Наборы строк IRowsetFastLoad  
 Драйвер OLE DB для SQL Server групповое копирование наборов строк доступны только для записи, но они предоставляют интерфейсы, позволяющие потребителю определить структуру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы. На включенным массовым копированием предоставлены следующие интерфейсы OLE DB для драйверов для набора строк SQL Server:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Специфический для поставщика свойства SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS и SSPROP_FASTLOADKEEPIDENTITY управляют поведения драйвера OLE DB для набора строк массового копирования SQL Server. Свойства указаны в *rgProperties* членом *rgPropertySets* **IOpenRowset** член параметра.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BOOL<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Поддерживает значения идентификаторов, указанные потребителем.<br /><br /> VARIANT_FALSE: Значения для столбца идентификаторов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы, созданные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Любое значение, привязанное к столбцу учитывается драйвером OLE DB для SQL Server.<br /><br /> VARIANT_TRUE: Потребитель привязывает метод доступа, указав значение для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] столбца идентификаторов. Свойство идентификатора недоступно для столбцов, допускающих значение NULL, так что потребитель предоставляет уникальное значение для каждого **IRowsetFastLoad::Insert** вызова.|  
|SSPROP_FASTLOADKEEPNULLS|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BOOL<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Поддерживает значение NULL для столбцов с ограничением по умолчанию. Затрагивает только столбцы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые допускают значение NULL и к которым применено ограничение DEFAULT.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вставляет значение по умолчанию для столбца, когда драйвер OLE DB для SQL Server потребителя вставляет строки, содержащей значение NULL для столбца.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вставит значение NULL для значения столбца, когда драйвер OLE DB для SQL Server потребителя вставляет строки, содержащей значение NULL для столбца.|  
|SSPROP_FASTLOADOPTIONS|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BSTR<br /><br /> По умолчанию: нет<br /><br /> Описание: Это свойство является таким же, как **-h** »*указание*[,... *n*]» параметр **bcp** программы. Следующие строки можно использовать в качестве параметров при массовом копировании данных в таблицу.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,... *n*]): порядок сортировки данных в файле данных. Производительность массового копирования увеличивается, если загружаемый файл данных упорядочен по кластеризованному индексу таблицы.<br /><br /> **ROWS_PER_BATCH** = *bb*: количество строк данных в каждом пакете (как *bb*). Сервер оптимизирует массовую загрузку в соответствии со значением *bb*. По умолчанию **ROWS_PER_BATCH** неизвестно.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: в килобайтах (КБ) данных в каждом пакете (значение cc). По умолчанию **KILOBYTES_PER_BATCH** неизвестно.<br /><br /> **Аргумент TABLOCK**: снятием блокировки уровня таблицы на время операции массового копирования. Применение этого параметра значительно повышает производительность, так как удержание блокировки только в течение операции массового копирования уменьшает вероятность конфликтов блокировок в таблице. Таблицы могут загружаться по нескольким клиентам параллельно, если таблица не имеет индексов и **TABLOCK** указано. По умолчанию работа блокировки определяется параметром таблицы **блокировка на массовую загрузку таблицы**.<br /><br /> **CHECK_CONSTRAINTS**: любые ограничения для *table_name* проверяются во время операции массового копирования. По умолчанию ограничения не учитываются.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует управление версиями строк для триггеров и версии строк сохраняются в хранилище версий в **tempdb**. Поэтому оптимизации массовой записи в журнал доступны даже при включенных триггерах. Перед массовым импортом пакета с большим количеством строк с включенными триггерами, может потребоваться увеличить размер **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Использование операций массового копирования, работающих с файлами  
 Драйвер OLE DB для SQL Server реализует **IBCPSession** интерфейс для предоставления поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] операций массового копирования. **IBCPSession** интерфейс реализует [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md), и [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)методы.  
  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для компонентов SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Свойства источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Оптимизация производительности массового импорта данных](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  

