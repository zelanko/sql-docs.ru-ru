---
title: "Создание индексов SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 395992ef9885bd38f72e8b18699a6fcbe11016aa
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="creating-sql-server-indexes"></a>Создание индексов SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **IIndexDefinition::CreateIndex** функцию, позволяющую потребителям определять новые индексы на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблиц.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента создает табличные индексы в качестве индексов или ограничений. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет право создания ограничений владельцу таблицы, владельцу базы данных и членам некоторых административных ролей. По умолчанию только владелец таблицы может создавать в ней индекс. Таким образом успех или сбой **CreateIndex** зависит не только от прав доступа пользователя приложения но и от типа создаваемого индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в *pwszName* членом *uName* объединения в *pTableID* параметра. *EKind* членом *pTableID* должен быть равен DBKIND_NAME.  
  
 *PIndexID* параметр может иметь значение NULL, и если да, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента создает уникальное имя для индекса. Потребитель может записать имя индекса, указав допустимый указатель на DBID в *ppIndexID* параметра.  
  
 Потребитель может указать имя индекса в виде строки символов Юникода в *pwszName* членом *uName* объединение *pIndexID* параметра. *EKind* членом *pIndexID* должен быть равен DBKIND_NAME.  
  
 Потребитель указывает столбец или столбцы, входящие в индекс, по имени. Для каждой структуры DBINDEXCOLUMNDESC, используемой в **CreateIndex**, *eKind* членом *pColumnID* должен быть равен DBKIND_NAME. Имя столбца указано как строку символов Юникода в *pwszName* членом *uName* объединения в *pColumnID*.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживают возрастающий порядок значений в индексе. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента возвращает E_INVALIDARG, если потребитель указывает значение DBINDEX_COL_ORDER_DESC в любой структуре DBINDEXCOLUMNDESC.  
  
 **CreateIndex** интерпретирует свойства индекса следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Управляет кластеризацией индексов.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать кластеризованный индекс для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает не более одного кластеризованного индекса в любой таблице.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать некластеризованный индекс на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.|  
|DBPROP_INDEX_FILLFACTOR|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: 0<br /><br /> Описание: Указывает долю страниц индекса, используемых для хранения данных. Дополнительные сведения см. в разделе [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md).<br /><br /> Тип варианта — VT_I4. Значение должно находиться в диапазоне от 1 до 100.|  
|DBPROP_INDEX_INITIALIZE|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|R Чтение и запись: чтение и запись<br /><br /> Значение по умолчанию — VARIANT_FALSE Описание: создает индекс в виде ссылочной целостности, ограничение PRIMARY KEY.<br /><br /> VARIANT_TRUE: Индекс создан для поддержки ограничения PRIMARY KEY таблицы. Столбцы не должны иметь значений NULL.<br /><br /> VARIANT_FALSE: Индекс не используется как ограничение PRIMARY KEY для значений строк в таблице.|  
|DBPROP_INDEX_SORTBOOKMARKS|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не поддерживает это свойство. Пытается установить свойство **CreateIndex** привести к возврату значения DB_S_ERRORSOCCURRED. *DwStatus* член структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Создает индекс в виде ограничения UNIQUE на определенном столбце или столбцах.<br /><br /> VARIANT_TRUE: Индекс используется для уникального ограничения значений строк в таблице.<br /><br /> VARIANT_FALSE: Индекс не уникального ограничения строк.|  
  
 В специфический для поставщика наборе свойств DBPROPSET_SQLSERVERINDEX [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет следующее свойство сведения источника данных.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Тип: VT_BOOL (чтения и записи)<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Если это свойство со значением VARIANT_TRUE IIndexDefinition::CreateIndex, в результате первичного XML-индекса, создается соответствующий индексированному столбцу. Если это свойство имеет значение VARIANT_TRUE, параметр cIndexColumnDescs должен быть равен 1. В противном случае возникает ошибка.|  
  
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
  
  
