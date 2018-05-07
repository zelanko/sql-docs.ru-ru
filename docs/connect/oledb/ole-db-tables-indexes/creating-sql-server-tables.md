---
title: Создание таблиц SQL Server | Документы Microsoft
description: Создание таблицы SQL Server с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- OLE DB Driver for SQL Server, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5497a74c256282fd14f7c5301f7eea4cfa9aa596
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-sql-server-tables"></a>Создание таблиц SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server предоставляет **ITableDefinition::CreateTable** функция, которая позволяет потребителям создавать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблиц. Потребители используют **CreateTable** для создания именованных потребителем постоянных таблиц, а также постоянных и временных таблиц с уникальными именами, созданные с помощью драйвера OLE DB для SQL Server.  
  
 Когда потребитель вызывает метод **ITableDefinition::CreateTable**, если значение свойства DBPROP_TBL_TEMPTABLE имеет значение VARIANT_TRUE, драйвер OLE DB для SQL Server создает для потребителя имя временной таблицы. Потребитель задает *pTableID* параметр **CreateTable** значение NULL. Временные таблицы с именами, сформированными драйвер OLE DB для SQL Server не отображаются в **ТАБЛИЦ** набора строк, но доступны через **IOpenRowset** интерфейса.  
  
 Когда потребители задают имя таблицы в *pwszName* членом *uName* объединения в *pTableID* параметра, драйвер OLE DB для SQL Server создает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]таблица с таким именем. Имя таблицы подчиняется ограничениям для имен таблиц, принятым в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], и может указывать на постоянную таблицу, а также локальную или глобальную временную таблицу. Дополнительные сведения см. в разделе [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md). *PpTableID* параметр может иметь значение NULL.  
  
 Драйвер OLE DB для SQL Server может формировать имена постоянных и временных таблиц. Когда потребитель задает *pTableID* параметра значение NULL, наборы *ppTableID* чтобы она указывала на допустимый DBID\*, драйвер OLE DB для SQL Server возвращает созданное имя таблицы в *pwszName* членом *uName* объединение DBID, на который ссылается значение *ppTableID*. Для создания временной, драйвер OLE DB для таблицы с именем SQL Server, потребитель включает свойство таблицы OLE DB DBPROP_TBL_TEMPTABLE в набор, на который ссылается свойство таблицы *rgPropertySets* параметра. Драйвер OLE DB для SQL Server со строгими именами временные таблицы являются локальными.  
  
 **CreateTable** возвращает значение DB_E_BADTABLEID, если *eKind* членом *pTableID* не указывает на DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Использование структуры DBCOLUMNDESC  
 Потребитель может задать тип данных столбца с помощью *pwszTypeName* члена или *wType* член. Если потребитель указывает тип данных в *pwszTypeName*, драйвер OLE DB для SQL Server пропускает значения *wType*.  
  
 При использовании *pwszTypeName* , потребитель задает тип данных с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имена типов данных. Допустимыми являются имена типов данных, возвращаемые в столбце TYPE_NAME набора строк схемы PROVIDER_TYPES.  
  
 Драйвер OLE DB для SQL Server распознает подмножество значений DBTYPE перечисления OLE DB *wType* член. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../oledb/ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** возвращает DB_E_BADTYPE, если потребитель *pTypeInfo* или *pclsid* указал тип данных столбца.  
  
 Потребитель указывает имя столбца в *pwszName* членом *uName* объединения структуры DBCOLUMNDESC *dbcid* член. Имя столбца задается в виде символьной строки в Юникоде. *EKind* членом *dbcid* должен быть равен DBKIND_NAME. **CreateTable** возвращает значение DB_E_BADCOLUMNID, если *eKind* является недопустимым, *pwszName* имеет значение NULL, или, если значение *pwszName* не является допустимым [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] идентификатор.  
  
 Все свойства столбцов доступны для всех столбцов, определенных в данной таблице. **CreateTable** может вернуть DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, если значения свойств устанавливаются в конфликте. **CreateTable** возвращает ошибку, если недопустимые значения свойств столбцов вызывают [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сбой при создании таблицы.  
  
 Свойства столбцов в структуре DBCOLUMNDESC интерпретируются следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R Чтение и запись: чтение и запись<br /><br /> Значение по умолчанию — VARIANT_FALSE Описание: задает свойство идентификатора для создаваемого столбца. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство идентификатора может иметь только один столбец таблицы. Задать свойству значение VARIANT_TRUE для более чем одного столбца приводит к ошибке, когда драйвер OLE DB для SQL Server пытается создать таблицу на сервере.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Свойство identity допустимо только для **целое**, **числовое**, и **десятичное** типов, когда масштаб равен 0. Задать свойству значение VARIANT_TRUE для любого другого типа данных столбца приводит к ошибке, когда драйвер OLE DB для SQL Server пытается создать таблицу на сервере.<br /><br /> Драйвер OLE DB для SQL Server возвращает значение DB_S_ERRORSOCCURRED, если свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и *dwOption* DBPROP_COL_NULLABLE не равен DBPROPOPTIONS_REQUIRED. DB_E_ERRORSOCCURRED возвращается в том случае, если свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и *dwOption* DBPROP_COL_NULLABLE равен DBPROPOPTIONS_REQUIRED. Столбец определен с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство identity и DBPROP_COL_NULLABLE *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ограничение по умолчанию для столбца.<br /><br /> *VValue* DBPROP может относиться любой из нескольких типов. *VValue.vt* должен задавать тип, несовместимый с типом данных столбца. Например, если столбец имеет тип DBTYPE_WSTR и для этого столбца задано значение по умолчанию BSTR N/A, эти два типа совместимы. Определять же значение по умолчанию в столбце, определенном типом DBTYPE_R8, возникнет ошибка, когда драйвер OLE DB для SQL Server пытается создать таблицу на сервере.|  
|DBPROP_COL_DESCRIPTION|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Свойство столбца DBPROP_COL_DESCRIPTION не реализуется драйвером OLE DB для SQL Server.<br /><br /> *DwStatus* структуры DBPROP возвращает значение DBPROPSTATUS_NOTSUPPORTED при попытке потребителя записать значение свойства.<br /><br /> Задание свойства не является неустранимой ошибкой для драйвера OLE DB для SQL Server. Если все остальные значения параметров допустимы, таблица [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет создана.|  
|DBPROP_COL_FIXEDLENGTH|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Драйвер OLE DB для SQL Server использует значение DBPROP_COL_FIXEDLENGTH для определения сопоставления типов данных, когда потребитель задает тип данных столбца с помощью *wType* структуры DBCOLUMNDESC. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../oledb/ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: При создании таблицы, драйвер OLE DB для SQL Server указывает, должен ли столбец принимать значения null, если свойство имеет значение. Когда свойство не задано, способность столбца принимать значения NULL определяется установленным по умолчанию параметром базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ANSI_NULLS.<br /><br /> Драйвер OLE DB для SQL Server — поставщик соответствует требованиям стандарта ISO. Подключенные сеансы ведут себя в соответствии со стандартом ISO. Если потребитель не задал свойство DBPROP_COL_NULLABLE, столбец принимает значения NULL.|  
|DBPROP_COL_PRIMARYKEY|R Чтение и запись: чтение и запись<br /><br /> Значение по умолчанию — VARIANT_FALSE Описание: когда значение VARIANT_TRUE, драйвер OLE DB для SQL Server создает столбец с ограничением PRIMARY KEY.<br /><br /> При задании в качестве свойства столбца только один столбец может определять это ограничение. Задать свойству значение VARIANT_TRUE для более чем один столбец возвращает сообщение об ошибке при попытке создать драйвер OLE DB для SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы.<br /><br /> Примечание: Потребитель может использовать **IIndexDefinition::CreateIndex** для создания ограничения PRIMARY KEY на несколько столбцов.<br /><br /> Драйвер OLE DB для SQL Server возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* DBPROP_COL_UNIQUE не равен DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED возвращается в том случае, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* DBPROP_COL_UNIQUE равен DBPROPOPTIONS_REQUIRED. Столбец определен с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство identity, а элементу DBPROP_COL_PRIMARYKEY *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Драйвер OLE DB для SQL Server возвращает ошибку, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE.<br /><br /> Драйвер OLE DB для SQL Server возвращает ошибку из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение PRIMARY KEY для столбца недопустимого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных. Невозможно определить ограничения PRIMARY KEY для столбцов, созданных с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных **бит**, **текст**, **ntext**, и **изображения**.|  
|DBPROP_COL_UNIQUE|R Чтение и запись: чтение и запись<br /><br /> Значение по умолчанию — VARIANT_FALSE Описание: применяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ограничение UNIQUE к столбцу.<br /><br /> При задании в качестве свойства столбца только к одному столбцу может быть применено это ограничение. Потребитель может использовать **IIndexDefinition::CreateIndex** для создания ограничения UNIQUE на сочетании значений нескольких столбцов.<br /><br /> Драйвер OLE DB для SQL Server возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED возвращается в том случае, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* равен DBPROPOPTIONS_REQUIRED. Столбец определен с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство identity, а элементу DBPROP_COL_PRIMARYKEY *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Драйвер OLE DB для SQL Server возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED возвращается в том случае, если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* равен DBPROPOPTIONS_REQUIRED. Столбец определен с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство identity и DBPROP_COL_NULLABLE *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> Драйвер OLE DB для SQL Server возвращает ошибку из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение УНИКАЛЬНОСТИ для столбца недопустимого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных. Невозможно определить ограничения UNIQUE для столбцов, созданных с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **бит** тип данных.|  
  
 Когда потребитель вызывает метод **ITableDefinition::CreateTable**, драйвер OLE DB для SQL Server интерпретирует свойства таблицы следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R Чтение и запись: чтение и запись<br /><br /> Значение по умолчанию — VARIANT_FALSE Описание: по умолчанию драйвер OLE DB для SQL Server создает таблицы, имена которых присваивает потребитель. Когда значение VARIANT_TRUE, драйвер OLE DB для SQL Server создает временное имя таблицы для объекта-получателя. Потребитель задает *pTableID* параметр **CreateTable** значение NULL. *PpTableID* параметр должен содержать допустимый указатель.|  
  
 Если потребитель запрашивает, набор строк открываться на успешно созданной таблицы, драйвер OLE DB для SQL Server открывает набор строк с поддержкой курсора. Все свойства набора строк могут быть заданы в передаваемых наборах свойств.  
  
 В данном примере создается таблица [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
