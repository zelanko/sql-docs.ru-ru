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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 72a278a142889d8b9d1e43976939f06b002689d7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069738"
---
# <a name="creating-sql-server-tables"></a>Создание таблиц SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ITableDefinition::CreateTable** функция, которая позволяет потребителям создавать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблиц. Потребители используют **CreateTable** для создания именованных потребителем постоянных таблиц, а также постоянных и временных таблиц с уникальными именами, созданными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
 Когда потребитель вызывает **ITableDefinition::CreateTable**, если значение свойства DBPROP_TBL_TEMPTABLE имеет значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента создает имя временной таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Временные таблицы с именами, сформированными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не отображаются в **ТАБЛИЦ** набора строк, но можно получить при помощи **IOpenRowset** интерфейс.  
  
 Когда потребители задают имя таблицы в *pwszName* членом *uName* объединения в *pTableID* параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента Создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы с таким именем. Имя таблицы подчиняется ограничениям для имен таблиц, принятым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и может указывать на постоянную таблицу, а также локальную или глобальную временную таблицу. Дополнительные сведения см. в разделе [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md). Параметр *ppTableID* может иметь значение NULL.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента можно формировать имена постоянных и временных таблиц. Когда потребитель устанавливает *pTableID* параметр значение NULL и наборы *ppTableID* указывал на допустимый DBID\*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента возвращает создаваемое имя в таблицу *pwszName* членом *uName* объединение DBID, на которые указывают значение *ppTableID*. Чтобы создать временный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу с именем поставщика OLE DB для собственного клиента, потребитель включает свойство таблицы OLE DB DBPROP_TBL_TEMPTABLE в набор, на которые имеются ссылки в свойств таблицы *rgPropertySets* параметра. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент OLE DB с именем поставщика временные таблицы являются локальными.  
  
 Функция **CreateTable** возвращает значение DB_E_BADTABLEID, если член *eKind* параметра *pTableID* не указывает на DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Использование структуры DBCOLUMNDESC  
 Потребитель может задать тип данных столбца либо с помощью переменной-члена *pwszTypeName*, либо с помощью переменной-члена *wType*. Если потребитель указывает тип данных в *pwszTypeName*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не учитывает значение *wType*.  
  
 Если используется переменная-член *pwszTypeName*, потребитель задает тип данных, используя имена типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допустимыми являются имена типов данных, возвращаемые в столбце TYPE_NAME набора строк схемы PROVIDER_TYPES.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента распознает подмножество значений DBTYPE перечисления OLE DB *wType* член. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  Функция **CreateTable** возвращает значение DB_E_BADTYPE, если потребитель указал тип данных столбца с помощью члена *pTypeInfo* или *pclsid*.  
  
 Пользователь задает имя столбца в элементе *pwszName* объединения *uName* в переменной-члене *dbcid* структуры DBCOLUMNDESC. Имя столбца задается в виде символьной строки в Юникоде. Элемент *eKind* структуры *dbcid* должен быть равен DBKIND_NAME. Функция **CreateTable** возвращает значение DB_E_BADCOLUMNID, если элемент *eKind* недопустим или значение *pwszName* равно NULL либо не является допустимым идентификатором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Все свойства столбцов доступны для всех столбцов, определенных в данной таблице. Функция **CreateTable** возвращает значение DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, если установленные значения свойств противоречат друг другу. Функция **CreateTable** возвращает ошибку, если недопустимые значения свойств столбцов вызывают ошибку при создании таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Свойства столбцов в структуре DBCOLUMNDESC интерпретируются следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE Описание: Задает свойство идентификатора для создаваемого столбца. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство идентификатора может иметь только один столбец таблицы. Свойству присвоено значение VARIANT_TRUE для нескольких столбцов, возникнет ошибка при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.<br /><br /> Свойство идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] действительно только для типов **integer**, **numeric** и **decimal**, когда масштаб равен 0. Свойству присвоено значение VARIANT_TRUE для столбца любого другого типа данных приводит к ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и *dwOption* свойства DBPROP_COL_NULLABLE не DBPROPOPTIONS_ Обязательно. Если оба свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_NULLABLE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: None<br /><br /> Описание. Создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничение по умолчанию для столбца.<br /><br /> Элемент *vValue* структуры DBPROP может относиться к любому типу из определенного набора типов. Элемент *vValue.vt* должен задавать тип, совместимый с типом данных столбца. Например, если столбец имеет тип DBTYPE_WSTR и для этого столбца задано значение по умолчанию BSTR N/A, эти два типа совместимы. Определение же значение по умолчанию на столбец, определенный как DBTYPE_R8 приводит к ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.|  
|DBPROP_COL_DESCRIPTION|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: None<br /><br /> Описание. Свойство столбца DBPROP_COL_DESCRIPTION не реализован [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.<br /><br /> Элемент *dwStatus* структуры DBPROP возвращает значение DBPROPSTATUS_NOTSUPPORTED при попытке потребителя записать значение свойства.<br /><br /> Задание свойства не является неустранимой ошибкой для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. Если все остальные значения параметров допустимы, таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет создана.|  
|DBPROP_COL_FIXEDLENGTH|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента использует значение DBPROP_COL_FIXEDLENGTH для определения сопоставления типов данных, когда потребитель задает тип данных столбца с помощью *wType* структуры DBCOLUMNDESC. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: None<br /><br /> Описание. При создании таблицы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента указывает, должен ли столбец принимать значения null, если свойство имеет значение. Когда свойство не задано, способность столбца принимать значения NULL определяется установленным по умолчанию параметром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента является поставщик соответствует требованиям стандарта ISO. Подключенные сеансы ведут себя в соответствии со стандартом ISO. Если потребитель не задал свойство DBPROP_COL_NULLABLE, столбец принимает значения NULL.|  
|DBPROP_COL_PRIMARYKEY|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE Описание: Если значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента создает столбец с ограничением PRIMARY KEY.<br /><br /> При задании в качестве свойства столбца только один столбец может определять это ограничение. Установка этого свойства в VARIANT_TRUE сложнее, чем один столбец возвращает сообщение об ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.<br /><br /> Примечание. Потребитель может использовать **IIndexDefinition::CreateIndex** для создания ограничения PRIMARY KEY на два или несколько столбцов.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* свойства DBPROP_COL_UNIQUE не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* свойства DBPROP_COL_UNIQUE равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение PRIMARY KEY для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных. Ограничения PRIMARY KEY нельзя определять для столбцов, относящихся к типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**, **text**, **ntext** и **image**.|  
|DBPROP_COL_UNIQUE|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE Описание: Применяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничение УНИКАЛЬНОСТИ для столбца.<br /><br /> При задании в качестве свойства столбца только к одному столбцу может быть применено это ограничение. Потребитель может использовать метод **IIndexDefinition::CreateIndex** с целью создания ограничения UNIQUE для сочетания значений нескольких столбцов.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_PRIMARYKEY *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и элемент *dwOption* равен DBPROPOPTIONS_REQUIRED, будет возвращено значение DB_E_ERRORSOCCURRED. Столбец определяется с помощью свойства идентификатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а элементу DBPROP_COL_NULLABLE *dwStatus* присваивается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение уникальности для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных. Ограничения UNIQUE нельзя определять для столбцов, относящихся к типу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.|  
  
 Когда потребитель вызывает **ITableDefinition::CreateTable**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента интерпретирует свойства таблицы следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE Описание: По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента создает таблицы, имена которых присваивает потребитель. Если значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента создает имя временной таблицы для потребителя. Потребитель задает для параметра *pTableID* метода **CreateTable** значение NULL. Параметр *ppTableID* должен содержать допустимый указатель.|  
  
 Если потребитель запрашивает, что открыть набор строк для успешно созданной таблицы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента открывает набор строк, поддерживаемый курсорами. Все свойства набора строк могут быть заданы в передаваемых наборах свойств.  
  
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
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
