---
title: Создание таблиц SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f3d1ae29828e18cf98941666e7884e70115ba39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301869"
---
# <a name="creating-sql-server-tables"></a>Создание таблиц SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет функцию **ITableDefinition::CreateTable,** позволяющую потребителям создавать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. Потребители используют **CreateTable** для создания постоянных таблиц с названием потребителя, а также постоянных или временных таблиц с уникальными именами, созданными поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.  
  
 Когда потребитель звонит **ITableDefinition::CreateTable**, если стоимость DBPROP_TBL_TEMPTABLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойства VARIANT_TRUE, поставщик Native Client OLE DB генерирует временное имя таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Временные таблицы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именами, генерируемыми поставщиком Native Client OLE DB, не отображаются в строке **TABLES,** но доступны через интерфейс **IOpenRowset.**  
  
 Когда потребители указывают имя таблицы в *pwszName* члена союза *uName* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметре *pTableID,* поставщик Native Client OLE DB создает таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с этим именем. Имя таблицы подчиняется ограничениям для имен таблиц, принятым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и может указывать на постоянную таблицу, а также локальную или глобальную временную таблицу. Для получения дополнительной информации [см.](../../t-sql/statements/create-table-transact-sql.md) Параметр *ppTableID* может иметь значение NULL.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может создавать названия постоянных или временных таблиц. Когда потребитель устанавливает параметр *pTableID* в NULL и устанавливает *ppTableID,* чтобы указать\*на действительный DBID, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает генерируемое имя таблицы в *pwszName* член союза *uName* DBID, на который указывает сярпридение *ppTableID.* Для создания временной таблицы, названной поставщиком native Client OLE DB, потребитель включает свойство таблицы OLE DB DBPROP_TBL_TEMPTABLE в свойство таблицы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на который ссылается параметр *rgPropertySets.* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Временные таблицы, названные поставщиком NATIVE Client OLE DB, являются локальными.  
  
 Функция **CreateTable** возвращает значение DB_E_BADTABLEID, если член *eKind* параметра *pTableID* не указывает на DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Использование структуры DBCOLUMNDESC  
 Потребитель может задать тип данных столбца либо с помощью переменной-члена *pwszTypeName*, либо с помощью переменной-члена *wType*. Если потребитель указывает тип данных в *pwszTypeName,* поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB игнорирует значение *wType.*  
  
 Если используется переменная-член *pwszTypeName*, потребитель задает тип данных, используя имена типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допустимыми являются имена типов данных, возвращаемые в столбце TYPE_NAME набора строк схемы PROVIDER_TYPES.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB распознает в члене *wType* значений DBTYPE, перечисленных в OLE DBTYPE. Дополнительные сведения см. в разделе [Сопоставление типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  Функция **CreateTable** возвращает значение DB_E_BADTYPE, если потребитель указал тип данных столбца с помощью члена *pTypeInfo* или *pclsid*.  
  
 Пользователь задает имя столбца в элементе *pwszName* объединения *uName* в переменной-члене *dbcid* структуры DBCOLUMNDESC. Имя столбца задается в виде символьной строки в Юникоде. Элемент *eKind* структуры *dbcid* должен быть равен DBKIND_NAME. **CreateTable** возвращается DB_E_BADCOLUMNID, если *eKind* является недействительным, *pwszName* является NULL, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если значение *pwszName* не является действительным идентификатором.  
  
 Все свойства столбцов доступны для всех столбцов, определенных в данной таблице. Функция **CreateTable** возвращает значение DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, если установленные значения свойств противоречат друг другу. Функция **CreateTable** возвращает ошибку, если недопустимые значения свойств столбцов вызывают ошибку при создании таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Свойства столбцов в структуре DBCOLUMNDESC интерпретируются следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE Описание: Устанавливает свойство идентификации в созданном столбце. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство идентификатора может иметь только один столбец таблицы. Установка свойства на VARIANT_TRUE для более чем одного столбца создает ошибку, когда поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB пытается создать таблицу на сервере.<br /><br /> Свойство идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] действительно только для типов **integer**, **numeric** и **decimal**, когда масштаб равен 0. Установка свойства на VARIANT_TRUE на столбец любого другого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа данных создает ошибку, когда поставщик Native Client OLE DB пытается создать таблицу на сервере.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращается DB_S_ERRORSOCCURRED, когда DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE VARIANT_TRUE и *dwOption* DBPROP_COL_NULLABLE не DBPROPOPTIONS_REQUIRED. Если оба свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_NULLABLE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: создает для столбца ограничение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DEFAULT.<br /><br /> Элемент *vValue* структуры DBPROP может относиться к любому типу из определенного набора типов. Элемент *vValue.vt* должен задавать тип, совместимый с типом данных столбца. Например, если столбец имеет тип DBTYPE_WSTR и для этого столбца задано значение по умолчанию BSTR N/A, эти два типа совместимы. Определение того же значения по умолчанию на столбце, определяемом как DBTYPE_R8 генерирует ошибку, когда поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB пытается создать таблицу на сервере.|  
|DBPROP_COL_DESCRIPTION|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: Свойство колонки DBPROP_COL_DESCRIPTION [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не реализуется поставщиком Native Client OLE DB.<br /><br /> Элемент *dwStatus* структуры DBPROP возвращает значение DBPROPSTATUS_NOTSUPPORTED при попытке потребителя записать значение свойства.<br /><br /> Установка свойства не является фатальной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибкой для поставщика Native Client OLE DB. Если все остальные значения параметров допустимы, таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет создана.|  
|DBPROP_COL_FIXEDLENGTH|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик Native Client OLE DB использует DBPROP_COL_FIXEDLENGTH для определения отображения типа данных, когда потребитель определяет тип данных столбца с помощью члена *wType* DBCOLUMNDESC. Дополнительные сведения см. в разделе [Сопоставление типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R/W: Читать/писать<br /><br /> По умолчанию: нет<br /><br /> Описание: При создании таблицы поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB указывает, должен ли столбец принимать нулевые значения, если свойство установлено. Когда свойство не задано, способность столбца принимать значения NULL определяется установленным по умолчанию параметром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB является поставщиком Услуг, соответствующих требованиям ISO. Подключенные сеансы ведут себя в соответствии со стандартом ISO. Если потребитель не задал свойство DBPROP_COL_NULLABLE, столбец принимает значения NULL.|  
|DBPROP_COL_PRIMARYKEY|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE Описание: Когда VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик NATIVE Client OLE DB создает столбец с ограничением PRIMARY KEY.<br /><br /> При задании в качестве свойства столбца только один столбец может определять это ограничение. Установка VARIANT_TRUE свойств для более чем одного столбца возвращает ошибку, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB пытается создать таблицу.<br /><br /> Примечание. Потребитель может использовать метод **IIndexDefinition::CreateIndex** для создания ограничения PRIMARY KEY для нескольких столбцов.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращается DB_S_ERRORSOCCURRED, когда DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE VARIANT_TRUE и *dwOption* of DBPROP_COL_UNIQUE не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_UNIQUE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает ошибку, когда DBPROP_COL_PRIMARYKEY и DBPROP_COL_NULLABLE VARIANT_TRUE.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, когда потребитель пытается создать ограничение PRIMARY [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] KEY на столбце недействительного типа данных. Ограничения PRIMARY KEY нельзя определять для столбцов, относящихся к типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**bit**, **text**, **ntext** и **image**.|  
|DBPROP_COL_UNIQUE|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Описание: применяет сяор у УНИКУЕ к столбцу.<br /><br /> При задании в качестве свойства столбца только к одному столбцу может быть применено это ограничение. Потребитель может использовать метод **IIndexDefinition::CreateIndex** с целью создания ограничения UNIQUE для сочетания значений нескольких столбцов.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращается DB_S_ERRORSOCCURRED, когда DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE VARIANT_TRUE и *dwOption* не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращается DB_S_ERRORSOCCURRED, когда DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE VARIANT_TRUE и *dwOption* не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, когда потребитель пытается создать ограничение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] УНИКУЭ на столбце недействительного типа данных. Ограничения UNIQUE нельзя определять для столбцов, относящихся к типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.|  
  
 Когда потребитель вызывает **ITableDefinition::CreateTable**, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB интерпретирует свойства таблицы следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W: Читать/писать<br /><br /> По умолчанию: VARIANT_FALSE Описание: По умолчанию поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB создает таблицы, названные потребителем. При VARIANT_TRUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB генерирует временное имя таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Параметр *ppTableID* должен содержать допустимый указатель.|  
  
 Если потребитель просит открыть набор строк на успешно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] созданной таблице, поставщик Native Client OLE DB открывает рядовые наборы с поддержкой курсора. Все свойства набора строк могут быть заданы в передаваемых наборах свойств.  
  
 В данном примере создается таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
