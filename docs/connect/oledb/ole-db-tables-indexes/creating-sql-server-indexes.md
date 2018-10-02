---
title: Создание индексов SQL Server | Документация Майкрософт
description: Создание индексов SQL Server, с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
- adding indexes
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: bdb8b8f48a4a54a185f6ffae03cf129e4549641b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612923"
---
# <a name="creating-sql-server-indexes"></a>Создание индексов SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет функцию **IIndexDefinition::CreateIndex**, позволяющую потребителям определять новые индексы в таблицах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Драйвер OLE DB для SQL Server создает табличные индексы в качестве индексов или ограничений. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет право создания ограничений владельцу таблицы, владельцу базы данных и членам некоторых административных ролей. По умолчанию только владелец таблицы может создавать в ней индекс. Таким образом, успех или сбой функции **CreateIndex** зависит не только от прав доступа пользователя приложения, но и от типа создаваемого индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Параметр *pIndexID* может иметь значение NULL, и в этом случае драйвер OLE DB для SQL Server создает для индекса уникальное имя. Потребитель может сам задать имя индекса, указав для DBID допустимый указатель в параметре *ppIndexID*.  
  
 Потребитель может задать имя индекса в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME.  
  
 Потребитель указывает столбец или столбцы, входящие в индекс, по имени. Для каждой структуры DBINDEXCOLUMNDESC, используемой в функции **CreateIndex**, элемент *eKind* параметра *pColumnID* должен быть DBKIND_NAME. Имя столбца задается в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* параметра *pColumnID*.  
  
 Драйвер OLE DB для SQL Server и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживают возрастающий порядок значений в индексе. Драйвер OLE DB для SQL Server возвращает значение E_INVALIDARG, если потребитель указывает значение DBINDEX_COL_ORDER_DESC в любой структуре DBINDEXCOLUMNDESC.  
  
 Функция **CreateIndex** интерпретирует свойства индекса указанным ниже образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|И запись: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: Управляет кластеризацией индексов.<br /><br /> VARIANT_TRUE: Драйвер OLE DB для SQL Server пытается создать кластеризованный индекс на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает не более одного кластеризованного индекса в любой таблице.<br /><br /> VARIANT_FALSE: Драйвер OLE DB для SQL Server пытается создать некластеризованный индекс на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы.|  
|DBPROP_INDEX_FILLFACTOR|И запись: чтение и запись<br /><br /> По умолчанию: 0<br /><br /> Описание: указывает процент страниц индекса, используемых для хранения. Дополнительные сведения см. в разделе [CREATE INDEX](../../../t-sql/statements/create-index-transact-sql.md).<br /><br /> Тип варианта — VT_I4. Значение должно находиться в диапазоне от 1 до 100.|  
|DBPROP_INDEX_INITIALIZE|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|И запись: чтение и запись<br /><br /> Значение по умолчанию — Значение VARIANT_FALSE Описание: создает индекс в виде ссылочной целостности, ограничение PRIMARY KEY.<br /><br /> VARIANT_TRUE: индекс создается для поддержки ограничения PRIMARY KEY таблицы. Столбцы не должны иметь значений NULL.<br /><br /> VARIANT_FALSE: индекс не используется в качестве ограничения PRIMARY KEY для значений строк таблицы.|  
|DBPROP_INDEX_SORTBOOKMARKS|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Драйвер OLE DB для SQL Server не поддерживает это свойство. Попытки установить свойство в **CreateIndex** приводят к возврату значения DB_S_ERRORSOCCURRED. Элемент *dwStatus* структуры свойства указывает значение DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|И запись: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: создает индекс в виде ограничения UNIQUE для определенного столбца или столбцов.<br /><br /> VARIANT_TRUE: индекс используется для уникального ограничения значений в строках таблицы.<br /><br /> VARIANT_FALSE: индекс не используется для уникального ограничения значений строк.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERINDEX драйвер OLE DB для SQL Server определяет указанное ниже свойство, хранящее информацию об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Тип: VT_BOOL (чтение/запись)<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: если при вызове метода IIndexDefinition::CreateIndex это свойство указывается со значением VARIANT_TRUE, создается первичный XML-индекс, соответствующий индексированному столбцу. Если это свойство имеет значение VARIANT_TRUE, параметр cIndexColumnDescs должен быть равен 1. В противном случае возникает ошибка.|  
  
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
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
