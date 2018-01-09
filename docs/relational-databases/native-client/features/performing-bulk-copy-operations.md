---
title: "Выполнение операций массового копирования | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk copy [SQL Server Native Client]
- data access [SQL Server Native Client], bulk copy operations
- SQL Server Native Client, bulk copy operations
- SQLNCLI, bulk copy operations
ms.assetid: 50d8456b-e6a1-4b25-bc7e-56946ed654a7
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c6070899aab81b6e3cef56a7c6320934d57a21d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="performing-bulk-copy-operations"></a>Выполнение операций массового копирования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Функция массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает передачу больших объемов данных в таблицу или представление [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или из них. Данные можно также передать путем указания инструкции SELECT. Данные можно передавать между [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и файлом данных операционной системы, таким как ASCII-файл. Файлы данных могут иметь различные форматы. Формат определяется для массового копирования в файле форматирования. По желанию данные можно загрузить в переменные программы и передать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью функций и методов массового копирования.  
  
 Образец приложения, демонстрирующий эту функцию, в разделе [массового копирования данных с помощью IRowsetFastLoad &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 Приложение обычно использует массовое копирование одним из следующих способов.  
  
-   Массовое копирование из таблицы, представления или результирующего набора инструкции Transact-SQL в файл данных, куда данные помещаются в том же формате, что и в таблице или представлении.  
  
     Такой файл называется файлом данных собственного режима.  
  
-   Массовое копирование из таблицы, представления или результирующего набора инструкции Transact-SQL в файл данных, куда данные помещаются в формате, отличном от формата в таблице или представлении.  
  
     В этом случае создается отдельный файл форматирования, который определяет характеристики (тип данных, позицию, длину, признак конца и т. д.) каждого столбца, когда он помещается в файл данных. Если все столбцы преобразуются в символьный формат, результирующий файл называется файлом данных символьного режима.  
  
-   Массовое копирование из файлов данных в таблицу или представление.  
  
     При необходимости файл форматирования используется для определения макета файла данных.  
  
-   Загрузите данные в переменные программы, а затем выполните импорт данных в таблицу или представление с помощью функций массового копирования для массового копирования по строке за раз.  
  
 Файлы данных, используемые функциями массового копирования, не приходится создавать при помощи другой программы массового копирования. Любая другая система может создать файл данных и файл форматирования в соответствии с определениями массового копирования. Эти файлы можно затем использовать в программе массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для импорта данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Например, можно экспортировать данные из электронной таблицы в файл с разделителями-символами табуляции, построить файл форматирования, описывающий файл с разделителями-символами табуляции, а затем использовать функции массового копирования для быстрого импорта данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Файлы данных, созданные при массовом копировании, можно также импортировать в другие приложения. Например, можно использовать функции массового копирования для экспорта данных из таблицы или представления в файл с разделителями-символами табуляции, который затем можно загрузить в электронную таблицу.  
  
 Программисты, пишущие приложения, использующие функции массового копирования, должны следовать основным правилам для обеспечения хорошей производительности массового копирования. Дополнительные сведения о поддержке операций массового копирования в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в разделе [массовый импорт и экспорт данных &#40; SQL Server &#41; ](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Определяемый пользователем тип данных CLR должен быть привязан как двоичные данные. Даже если файл форматирования указывает SQLCHAR как тип данных для целевого столбца определяемого пользователем типа, программа bcp будет рассматривать данные как двоичные.  
  
 Нельзя использовать инструкцию SET FMTONLY OFF с операциями массового копирования. Ее использование может стать причиной завершения операции массового копирования с ошибкой или получению непредвиденных результатов.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента реализует два метода для выполнения операций массового копирования с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных. Первый метод предполагает использование [IRowsetFastLoad](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) интерфейс на основе памяти массовое копирование; и второй предполагает использование [IBCPSession](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md) интерфейс для операций массового копирования.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Использование операций массового копирования, работающих с памятью  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Реализует поставщик OLE DB для собственного клиента **IRowsetFastLoad** интерфейс для предоставления поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] операций на основе памяти массового копирования. **IRowsetFastLoad** интерфейс реализует [IRowsetFastLoad::Commit](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) и [IRowsetFastLoad::InsertRow](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md) методы.  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Включение сеанса для метода IRowsetFastLoad  
 Потребитель уведомляет поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] о необходимости массового копирования путем установки для свойства источника данных SSPROP_ENABLEFASTLOAD, зависящего от поставщика OLE DB для собственного клиента OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], значения VARIANT_TRUE. При задании свойства на источник данных потребитель создает сеанс поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Новый сеанс позволяет потребителю получить доступ к **IRowsetFastLoad** интерфейса.  
  
> [!NOTE]  
>  Если **IDataInitialize** интерфейса используется для инициализации источника данных, то необходимо задать свойство SSPROP_IRowsetFastLoad *rgPropertySets* параметр  **IOpenRowset::OpenRowset** метод; в противном случае вызов **OpenRowset** метод возвращает ошибку E_NOINTERFACE.  
  
 Включение сеанса для массового копирования ограничивает поддержку интерфейсов в сеансе со стороны поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Сеанс с включенным массовым копированием предоставляет только следующие интерфейсы:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **Интерфейс ITransactionJoin**  
  
 Чтобы отключить создание набора строк с включенным массовым копированием и вернуть сеанс поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] к обычной обработке, задайте для свойства SSPROP_ENABLEFASTLOAD значение VARIANT_FALSE.  
  
#### <a name="irowsetfastload-rowsets"></a>Наборы строк IRowsetFastLoad  
 Наборы строк для массового копирования поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] доступны только для записи, но они предоставляют интерфейсы, позволяющие потребителю определить структуру таблицы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для набора строк поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с включенным массовым копированием предоставлены следующие интерфейсы:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **Интерфейс IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Свойства SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS и SSPROP_FASTLOADKEEPIDENTITY, зависящие от поставщика, управляют режимом работы набора строк для массового копирования поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Свойства указаны в *rgProperties* членом *rgPropertySets***IOpenRowset**член параметра.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BOOL<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Поддерживает значения идентификаторов, указанные потребителем.<br /><br /> VARIANT_FALSE: Значения для столбца идентификаторов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы, созданные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Любое значение, привязанное к обрабатывает этот столбец [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.<br /><br /> VARIANT_TRUE: Потребитель привязывает метод доступа, указав значение для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] столбца идентификаторов. Свойство идентификатора недоступно для столбцов, допускающих значение NULL, так что потребитель предоставляет уникальное значение для каждого **IRowsetFastLoad::Insert** вызова.|  
|SSPROP_FASTLOADKEEPNULLS|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BOOL<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Поддерживает значение NULL для столбцов с ограничением по умолчанию. Затрагивает только столбцы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые допускают значение NULL и к которым применено ограничение DEFAULT.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вставляет значение по умолчанию для столбца при вставке потребителем поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] строки, содержащей значение NULL для столбца.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вставляет значение NULL для значения столбца при вставке потребителем поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] строки, содержащей значение NULL для столбца.|  
|SSPROP_FASTLOADOPTIONS|Столбец: нет<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Тип: VT_BSTR<br /><br /> По умолчанию: нет<br /><br /> Описание: Это свойство является таким же, как **-h** »*указание*[,... *n* ]» параметр **bcp** программы. Следующие строки можно использовать в качестве параметров при массовом копировании данных в таблицу.<br /><br /> **ПОРЯДОК**(*столбца*[**ASC** &#124; **DESC**] [,... *n* ]): Порядок сортировки данных в файле данных. Производительность массового копирования увеличивается, если загружаемый файл данных упорядочен по кластеризованному индексу таблицы.<br /><br /> **ROWS_PER_BATCH** = *bb*: количество строк данных в каждом пакете (как *bb*). Сервер оптимизирует массовую загрузку в соответствии со значением *bb*. По умолчанию **ROWS_PER_BATCH** неизвестно.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: в килобайтах (КБ) данных в каждом пакете (значение cc). По умолчанию **KILOBYTES_PER_BATCH** неизвестно.<br /><br /> **Аргумент TABLOCK**: снятием блокировки уровня таблицы на время операции массового копирования. Применение этого параметра значительно повышает производительность, так как удержание блокировки только в течение операции массового копирования уменьшает вероятность конфликтов блокировок в таблице. Таблицы могут загружаться по нескольким клиентам параллельно, если таблица не имеет индексов и **TABLOCK** указано. По умолчанию работа блокировки определяется параметром таблицы **блокировка на массовую загрузку таблицы**.<br /><br /> **CHECK_CONSTRAINTS**: любые ограничения для *table_name* проверяются во время операции массового копирования. По умолчанию ограничения не учитываются.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует управление версиями строк для триггеров и версии строк сохраняются в хранилище версий в **tempdb**. Поэтому оптимизации массовой записи в журнал доступны даже при включенных триггерах. Перед массовым импортом пакета с большим количеством строк с включенными триггерами, может потребоваться увеличить размер **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Использование операций массового копирования, работающих с файлами  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Реализует поставщик OLE DB для собственного клиента **IBCPSession** интерфейс для предоставления поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] операций массового копирования. **IBCPSession** интерфейс реализует [IBCPSession::BCPColFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md), и [IBCPSession::BCPWriteFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)методы.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обеспечивает такую же поддержку операций массового копирования, которые были частью предыдущих версий драйвера ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения об операциях массового копирования с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента в разделе [выполнение операций массового копирования &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Свойства источника данных &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Оптимизация производительности массового импорта данных](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  
  
  
