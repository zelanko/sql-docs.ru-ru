---
title: Создание индексов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5770c54e748ab7658acb3319e1e1c3b56a8c178f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301675"
---
# <a name="creating-sql-server-indexes"></a>Создание индексов SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет функцию **IIndexDefinition::CreateIndex,** позволяющую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителям определять новые индексы в таблицах.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB создает индексы таблиц как индексы или ограничения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет право создания ограничений владельцу таблицы, владельцу базы данных и членам некоторых административных ролей. По умолчанию только владелец таблицы может создавать в ней индекс. Таким образом, успех или сбой функции **CreateIndex** зависит не только от прав доступа пользователя приложения, но и от типа создаваемого индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Параметр *pIndexID* может быть NULL, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если это так, то поставщик Native Client OLE DB создает уникальное название для индекса. Потребитель может сам задать имя индекса, указав для DBID допустимый указатель в параметре *ppIndexID*.  
  
 Потребитель может задать имя индекса в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME.  
  
 Потребитель указывает столбец или столбцы, входящие в индекс, по имени. Для каждой структуры DBINDEXCOLUMNDESC, используемой в функции **CreateIndex**, элемент *eKind* параметра *pColumnID* должен быть DBKIND_NAME. Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pColumnID*.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB и поддержка возрастающего порядка на значениях индекса. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает E_INVALIDARG если потребитель указывает DBINDEX_COL_ORDER_DESC в любой структуре DBINDEXCOLUMNDESC.  
  
 Функция **CreateIndex** интерпретирует свойства индекса указанным ниже образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: Контролирует кластеризм индексов.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик NATIVE Client OLE DB пытается создать кластерный индекс на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столе. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает не более одного кластеризованного индекса в любой таблице.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик NATIVE Client OLE DB пытается создать некластерный индекс на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столе.|  
|DBPROP_INDEX_FILLFACTOR|R/W: Читать/писать<br /><br /> По умолчанию: 0<br /><br /> Описание: указывает процент страниц индекса, используемых для хранения. Дополнительные сведения см. в разделе [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md).<br /><br /> Тип варианта — VT_I4. Значение должно находиться в диапазоне от 1 до 100.|  
|DBPROP_INDEX_INITIALIZE|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE Описание: Создает индекс как референциальную целостность, PRIMARY KEY ограничение.<br /><br /> VARIANT_TRUE: индекс создается для поддержки ограничения PRIMARY KEY таблицы. Столбцы не должны иметь значений NULL.<br /><br /> VARIANT_FALSE: индекс не используется в качестве ограничения PRIMARY KEY для значений строк таблицы.|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: создает индекс в виде ограничения UNIQUE для определенного столбца или столбцов.<br /><br /> VARIANT_TRUE: индекс используется для уникального ограничения значений в строках таблицы.<br /><br /> VARIANT_FALSE: индекс не используется для уникального ограничения значений строк.|  
  
 В наборе свойств, установленных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для поставщиков, DBPROPSET_SQLSERVERINDEX поставщик Native Client OLE DB определяет свойство следующего источника данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Тип: VT_BOOL (R/W)<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: если при вызове метода IIndexDefinition::CreateIndex это свойство указывается со значением VARIANT_TRUE, создается первичный XML-индекс, соответствующий индексированному столбцу. Если это свойство имеет значение VARIANT_TRUE, параметр cIndexColumnDescs должен быть равен 1. В противном случае возникает ошибка.|  
  
 В данном примере создается индекс первичного ключа.  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
