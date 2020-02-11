---
title: Создание таблиц SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e780a04f59bacba5063ac0bd6e9b7f3c74fd211a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046403"
---
# <a name="creating-sql-server-tables"></a>Создание таблиц SQL Server
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB предоставляет функцию **ITableDefinition:: CreateTable** , позволяющую потребителям создавать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. Потребители используют **CreateTable** для создания постоянных таблиц с именами потребителей, а также для постоянных или временных таблиц с уникальными именами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , созданными поставщиком OLE DB собственного клиента.  
  
 Когда потребитель вызывает **ITableDefinition:: CreateTable**, если значение свойства DBPROP_TBL_TEMPTABLE VARIANT_TRUE, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента создает имя временной таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Временные таблицы с именами, созданными поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента, не отображаются в наборе строк **Tables** , но доступны через интерфейс **IOpenRowset** .  
  
 Когда потребители задают имя таблицы в члене *pwszName* объединения *uname* в параметре *PTableID* , поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу с таким именем. Имя таблицы подчиняется ограничениям для имен таблиц, принятым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и может указывать на постоянную таблицу, а также локальную или глобальную временную таблицу. Дополнительные сведения см. в разделе [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql). Параметр *ppTableID* может иметь значение NULL.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента может создавать имена постоянных или временных таблиц. Когда потребитель устанавливает для параметра *pTableID* значение NULL и задает *ppTableID* для указания на допустимый\*DBID, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Возвращает созданное имя таблицы в *pwszName* члене *uname* объединения DBID, на которое указывает значение *ppTableID*. Чтобы создать временную, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственную клиентскую OLE DBную таблицу с именем поставщика, потребитель включает свойство таблицы OLE DB DBPROP_TBL_TEMPTABLE в набор свойств таблицы, указанный в параметре *rgPropertySets* . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента — именованные временные таблицы являются локальными.  
  
 **CreateTable** возвращает DB_E_BADTABLEID, если элемент *элемент ekind* параметра *pTableID* не указывает DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Использование структуры DBCOLUMNDESC  
 Потребитель может задать тип данных столбца либо с помощью переменной-члена *pwszTypeName*, либо с помощью переменной-члена *wType*. Если потребитель указывает тип данных в *pwszTypeName*, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента игнорирует значение *wType*.  
  
 Если используется переменная-член *pwszTypeName*, потребитель задает тип данных, используя имена типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допустимыми являются имена типов данных, возвращаемые в столбце TYPE_NAME набора строк схемы PROVIDER_TYPES.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента распознает подмножество значений DbType OLE DB перечисления в элементе *wType* . Дополнительные сведения см. [в разделе Сопоставление типов данных в ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** возвращает DB_E_BADTYPE, если потребитель устанавливает элемент *птипеинфо* или *пклсид* для указания типа данных столбца.  
  
 Пользователь задает имя столбца в элементе *pwszName* объединения *uName* в переменной-члене *dbcid* структуры DBCOLUMNDESC. Имя столбца задается в виде символьной строки в Юникоде. Элемент *eKind* структуры *dbcid* должен быть равен DBKIND_NAME. **CreateTable** возвращает DB_E_BADCOLUMNID, если *элемент ekind* является недопустимым, *pwszName* имеет значение null или если значение *pwszName* не является допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатором.  
  
 Все свойства столбцов доступны для всех столбцов, определенных в данной таблице. **CreateTable** может возвращать DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, если значения свойств установлены в конфликте. **CreateTable** возвращает ошибку, если недопустимые параметры свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца вызывают сбой при создании таблицы.  
  
 Свойства столбцов в структуре DBCOLUMNDESC интерпретируются следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VARIANT_FALSE Description: задает свойство Identity для созданного столбца. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство идентификатора может иметь только один столбец таблицы. Если присвоить свойству значение VARIANT_TRUE более чем для одного столбца, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при попытке поставщика OLE DB собственного клиента создать таблицу на сервере будет возникнет ошибка.<br /><br /> Свойство идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] действительно только для типов **integer**, **numeric** и **decimal**, когда масштаб равен 0. Присвоение свойству значения VARIANT_TRUE для столбца любого другого типа данных приводит к ошибке, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда поставщик собственного клиента OLE DB пытается создать таблицу на сервере.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает DB_S_ERRORSOCCURRED, если DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE являются VARIANT_TRUE, а *элемент dwoption* DBPROP_COL_NULLABLE не DBPROPOPTIONS_REQUIRED. Если оба свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_NULLABLE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|Чтение и запись в R/W<br /><br /> По умолчанию: нет<br /><br /> Описание: создает для столбца ограничение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DEFAULT.<br /><br /> Элемент *vValue* структуры DBPROP может относиться к любому типу из определенного набора типов. Элемент *vValue.vt* должен задавать тип, совместимый с типом данных столбца. Например, если столбец имеет тип DBTYPE_WSTR и для этого столбца задано значение по умолчанию BSTR N/A, эти два типа совместимы. Определение того же значения по умолчанию для столбца, определенного DBTYPE_R8, приводит к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибке при попытке поставщика OLE DB собственного клиента создать таблицу на сервере.|  
|DBPROP_COL_DESCRIPTION|Чтение и запись в R/W<br /><br /> По умолчанию: нет<br /><br /> Описание: свойство столбца DBPROP_COL_DESCRIPTION не реализовано поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB.<br /><br /> Элемент *dwStatus* структуры DBPROP возвращает значение DBPROPSTATUS_NOTSUPPORTED при попытке потребителя записать значение свойства.<br /><br /> Установка свойства не является неустранимой ошибкой для поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB. Если все остальные значения параметров допустимы, таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет создана.|  
|DBPROP_COL_FIXEDLENGTH|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Описание. поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента использует DBPROP_COL_FIXEDLENGTH для определения сопоставления типов данных, когда потребитель определяет тип данных столбца с помощью элемента *wType* объекта DBCOLUMNDESC. Дополнительные сведения см. [в разделе Сопоставление типов данных в ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|Чтение и запись в R/W<br /><br /> По умолчанию: нет<br /><br /> Описание: при создании таблицы поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB указывает, должен ли столбец принимать значения NULL, если свойство задано. Когда свойство не задано, способность столбца принимать значения NULL определяется установленным по умолчанию параметром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента является поставщиком, совместимым с ISO. Подключенные сеансы ведут себя в соответствии со стандартом ISO. Если потребитель не задал свойство DBPROP_COL_NULLABLE, столбец принимает значения NULL.|  
|DBPROP_COL_PRIMARYKEY|Чтение и запись в R/W<br /><br /> По умолчанию: VARIANT_FALSE Description: при VARIANT_TRUE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента создает столбец с ОГРАНИЧЕНИЕм первичного ключа.<br /><br /> При задании в качестве свойства столбца только один столбец может определять это ограничение. Установка свойства VARIANT_TRUE для более чем одного столбца возвращает ошибку, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда поставщик собственного клиента OLE DB пытается создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу.<br /><br /> Примечание. Потребитель может использовать метод **IIndexDefinition::CreateIndex** для создания ограничения PRIMARY KEY для нескольких столбцов.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает DB_S_ERRORSOCCURRED, если DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE являются VARIANT_TRUE, а *элемент dwoption* DBPROP_COL_UNIQUE не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_UNIQUE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает ошибку, когда DBPROP_COL_PRIMARYKEY и DBPROP_COL_NULLABLE оба VARIANT_TRUE.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает ошибку, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда потребитель ПЫТАЕТся создать ограничение первичного ключа для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа данных. Ограничения PRIMARY KEY нельзя определять для столбцов, относящихся к типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**bit**, **text**, **ntext** и **image**.|  
|DBPROP_COL_UNIQUE|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VARIANT_FALSE Description [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : применяет к столбцу ограничение UNIQUE.<br /><br /> При задании в качестве свойства столбца только к одному столбцу может быть применено это ограничение. Потребитель может использовать метод **IIndexDefinition::CreateIndex** с целью создания ограничения UNIQUE для сочетания значений нескольких столбцов.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает DB_S_ERRORSOCCURRED, если DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE являются VARIANT_TRUE и *элемент dwoption* не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает DB_S_ERRORSOCCURRED, если DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE являются VARIANT_TRUE и *элемент dwoption* не DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает ошибку, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда потребитель ПЫТАЕТся создать ограничение UNIQUE для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа данных. Ограничения UNIQUE нельзя определять для столбцов, относящихся к типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.|  
  
 Когда потребитель вызывает **ITableDefinition:: CreateTable**, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента интерпретирует свойства таблицы следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VARIANT_FALSE Description: по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] умолчанию поставщик OLE DB собственного клиента создает таблицы с именами, указанными потребителем. При VARIANT_TRUE поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента создает имя временной таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Параметр *ppTableID* должен содержать допустимый указатель.|  
  
 Если потребитель запрашивает открытие набора строк в успешно созданной таблице, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента открывает набор строк, поддерживающий курсоры. Все свойства набора строк могут быть заданы в передаваемых наборах свойств.  
  
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
  
  
