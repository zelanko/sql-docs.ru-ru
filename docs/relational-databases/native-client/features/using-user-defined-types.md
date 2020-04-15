---
title: Использование пользовательских типов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [SQL Server Native Client]
- user-defined types [SQL Server], SQL Server Native Client
- SQL Server Native Client OLE DB provider, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- SQLNCLI, user-defined types
- SQL Server Native Client, user-defined types
- data access [SQL Server Native Client], user-defined types
- ISSCommandWithParameters interface
ms.assetid: e15d8169-3517-4323-9c9e-0f5c34aff7df
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4c6b6cf14925b7baace60a7de6c7aeaf3057de46
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303245"
---
# <a name="using-user-defined-types"></a>Использование определяемых пользователем типов данных
[!INCLUDE[appliesto-ss-asdb-xxxx-pdw-md](../../../includes/appliesto-ss-asdb-xxxx-pdw-md.md)]

  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] представлены определяемые пользователем типы данных (UDT). Пользовательские типы расширяют систему типов SQL путем разрешения хранения объектов и пользовательских структур данных в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Определяемые пользователем типы могут содержать несколько типов данных, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Определяемые пользователем типы определяются с помощью любого языка, поддерживаемого средой .NET CLR, который создает поддающийся проверке код. Это включает в себя Microsoft Visual C<sup>®</sup> и Visual Basic<sup>®</sup> .NET. Данные представляются в виде полей и свойств класса или структуры .NET, а поведения определяются методами класса или структуры.  
  
 Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает UDT как двоичные типы с информацией о метаданных, что позволяет управлять UDT в качестве объектов. Столбцы пользовательских типов представляются как DBTYPE_UDT, и их метаданные доступны через основной интерфейс OLE DB **IColumnRowset** и новый интерфейс [ISSCommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md).  
  
> [!NOTE]  
>  Метод **IRowsetFind::FindNextRow** не работает с пользовательским типом данных. Если определяемый пользователем тип используется в качестве типа столбца поиска, возвращается значение DB_E_BADCOMPAREOP.  
  
### <a name="data-bindings-and-coercions"></a>Привязки данных и приведение типов  
 В следующей таблице описаны привязка и приведение типа данных, которые возникают при использовании перечисленных определенных пользователем типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Колонки UDT подвергаются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через поставщика Native Client OLE DB в качестве DBTYPE_UDT. Метаданные можно получать через соответствующие наборы строк схемы, так что можно управлять собственными определенными типами как объектами.  
  
|Тип данных|На сервер<br /><br /> **Udt**|На сервер<br /><br /> **Не пользовательский тип**|С сервера<br /><br /> **Udt**|С сервера<br /><br /> **Не пользовательский тип**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|Поддерживается<sup>6</sup>|Ошибка<sup>1</sup>|Поддерживается<sup>6</sup>|Ошибка<sup>5</sup>|  
|DBTYPE_BYTES|Поддерживается<sup>6</sup>|Н/Д<sup>2</sup>|Поддерживается<sup>6</sup>|Н/Д<sup>2</sup>|  
|DBTYPE_WSTR|Поддерживается<sup>3,6</sup>|Н/Д<sup>2</sup>|Поддерживается<sup>4,6</sup>|Н/Д<sup>2</sup>|  
|DBTYPE_BSTR|Поддерживается<sup>3,6</sup>|Н/Д<sup>2</sup>|Поддерживается<sup>4</sup>|Н/Д<sup>2</sup>|  
|DBTYPE_STR|Поддерживается<sup>3,6</sup>|Н/Д<sup>2</sup>|Поддерживается<sup>4,6</sup>|Н/Д<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Не поддерживается|Н/Д<sup>2</sup>|Не поддерживается|Н/Д<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Поддерживается<sup>6</sup>|Н/Д<sup>2</sup>|Поддерживается<sup>4</sup>|Н/Д<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Поддерживается<sup>3,6</sup>|Н/Д<sup>2</sup>|Н/Д|Н/Д<sup>2</sup>|  
  
 <sup>1</sup>Если тип сервера, отличный от DBTYPE_UDT, указывается с помощью метода **ICommandWithParameters::SetParameterInfo** и типом метода доступа является DBTYPE_UDT, то при выполнении инструкции возникает ошибка (DB_E_ERRORSOCCURRED; состояние параметра — DBSTATUS_E_BADACCESSOR). В остальных случаях данные отсылаются на сервер, но сервер возвращает ошибку, указывающую на то, что нет неявного преобразования определяемого пользовательского типа в тип данных параметра.  
  
 <sup>2</sup> Вне сферы этой темы.  
  
 <sup>3</sup> Происходит преобразование шестнадцатеричной строки в двоичные данные.  
  
 <sup>4</sup> Происходит преобразование двоичных данных в шестнадцатеричную строку.  
  
 <sup>5</sup>Во время создания метода доступа или во время выборки может произойти проверка данных. Ошибка — DB_E_ERRORSOCCURRED, состояние привязки устанавливается в значение DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>6</sup>Может использоваться BY_REF.  
  
 Типы DBTYPE_NULL и DBTYPE_EMPTY могут быть привязаны только для входных параметров. Они не могут быть привязаны для выходных параметров или результатов. При привязке входных параметров состояние должно быть установлено в значение DBSTATUS_S_ISNULL или DBSTATUS_S_DEFAULT.  
  
 Тип DBTYPE_UDT также может быть преобразован в типы DBTYPE_EMPTY и DBTYPE_NULL, но тип DBTYPE_NULL и DBTYPE_EMPTY нельзя преобразовать в тип DBTYPE_UDT. Это правило обеспечивает согласование с DBTYPE_BYTES.  
  
> [!NOTE]  
>  Новый интерфейс **ISSCommandWithParameters**, наследуемый от интерфейса **ICommandWithParameters**, используется для работы с пользовательскими типами как с параметрами. Приложения должны использовать этот интерфейс для установки, по крайней мере, атрибута SSPROP_PARAM_UDT_NAME набора свойств DBPROPSET_SQLSERVERPARAMETER для параметров определяемых пользователем типов. Если это не сделано, метод **ICommand::Execute** возвратит ошибку DB_E_ERRORSOCCURRED. Этот интерфейс и набор свойств описан далее в этом разделе.  
  
 Если определяемый пользователем тип вставлен в столбец, который недостаточно велик для хранения всех его данных, метод **ICommand::Execute** вернет S_OK с состоянием DB_E_ERRORSOCCURRED.  
  
 Преобразования данных, выполняемые основными службами OLE DB (**IDataConvert**), неприменимы к типу DBTYPE_UDT. Другие привязки не поддерживаются.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Добавления и изменения для наборов строк OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Родной клиент добавляет новые значения или изменения во многие основные строки схемOLE DB.  
  
#### <a name="the-procedure_parameters-schema-rowset"></a>Набор строк схемы PROCEDURE_PARAMETERS  
 В набор строк схемы PROCEDURE_PARAMETERS были сделаны следующие добавления.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.|  
|SS_UDT_NAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Полное имя сборки, которое включает имя типа и все идентификационные данные сборки, необходимые для ссылки на сборку из среды CLR.|  
  
#### <a name="the-sql_assemblies-schema-rowset"></a>Набор строк схемы SQL_ASSEMBLIES  
 Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет новому поставщику специальную схему, описывая зарегистрированные UDT. Сервер ASSEMBLY может быть указан как тип DBTYPE_WSTR, но он отсутствует в наборе строк. Если значение не задано, то по умолчанию для набора строк будет использоваться текущий сервер. Набор строк схемы SQL_ASSEMBLIES определен в следующей таблице.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Имя каталога сборки, содержащей тип.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Имя схемы или имя владельца сборки, содержащей тип. Хотя сборки ограничены базой данных, а не схемой, они все еще имеют владельца, отраженного здесь.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Имя сборки, содержащей тип.|  
|ASSEMBLY_ID|DBTYPE_UI4|Идентификатор объекта сборки, содержащей тип.|  
|PERMISSION_SET|DBTYPE_WSTR|Значение, определяющее область доступа сборки. Значения включают «SAFE», «EXTERNAL_ACCESS» и «UNSAFE».|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Двоичное представление сборки.|  
  
#### <a name="the-sql_assemblies_-dependencies-schema-rowset"></a>Набор строк схемы SQL_ASSEMBLIES_ DEPENDENCIES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Поставщик Native Client OLE DB предоставляет новую схему, описываемую зависимости сборки для определенного сервера. ASSEMBLY_SERVER может быть указан участником как тип DBTYPE_WSTR, но отсутствовать в наборе строк. Если значение не задано, то по умолчанию для набора строк будет использоваться текущий сервер. Набор строк схемы SQL_ASSEMBLY_DEPENDENCIES определен в следующей таблице.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Имя каталога сборки, содержащей тип.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Имя схемы или имя владельца сборки, содержащей тип. Хотя сборки ограничены базой данных, а не схемой, они все еще имеют владельца, отраженного здесь.|  
|ASSEMBLY_ID|DBTYPE_UI4|Идентификатор объекта сборки.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|Идентификатор объекта сборки, на которую присутствует ссылка.|  
  
#### <a name="the-sql_user_types-schema-rowset"></a>Набор строк схемы SQL_USER_TYPES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Поставщик Native Client OLE DB предоставляет новую схему rowset, SQL_USER_TYPES, которая описывает, когда регистрируются UDT для определенного сервера. UDT_SERVER должен быть указан участником как тип DBTYPE_WSTR, но отсутствовать в наборе строк. Набор строк схемы SQL_USER_TYPES определен в следующей таблице.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Для столбцов определяемого пользователем типа данное свойство содержит строку, представляющую имя каталога, в котором определен этот тип.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Для столбцов определяемого пользователем типа данное свойство содержит строку, представляющую имя схемы, в которой определен этот тип.|  
|UDT_NAME|DBTYPE_WSTR|Имя сборки, содержащей класс определяемого пользователем типа.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Полное имя типа (AQN) включает имя типа и префикс пространства имен (если оно задано).|  
  
#### <a name="the-columns-schema-rowset"></a>Набор строк схемы COLUMNS  
 Добавления в наборе строк схемы COLUMNS включает следующие столбцы.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Для столбцов определяемого пользователем типа данное свойство содержит строку, представляющую имя каталога, в котором определен этот тип.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Для столбцов определяемого пользователем типа данное свойство содержит строку, представляющую имя схемы, в которой определен этот тип.|  
|SS_UDT_NAME|DBTYPE_WSTR|Имя определяемого пользователем типа.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Полное имя типа (AQN) включает имя типа и префикс пространства имен (если оно задано).|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Добавления и изменения для наборов свойств OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Родной клиент добавляет новые значения или изменения во многие основные наборы свойств OLE DB.  
  
#### <a name="the-dbpropset_sqlserverparameter-property-set"></a>Набор свойств DBPROPSET_SQLSERVERPARAMETER  
 Для поддержки UDT через OLE [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DB, Native Client реализует новый набор свойств DBPROPSET_SQLSERVERPARAMETER, содержащий следующие значения.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.<br /><br /> Для параметров определяемого пользователем типа это свойство содержит строку, представляющую имя каталога, в котором определен этот тип.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.<br /><br /> Для параметров определяемого пользователем типа данное свойство содержит строку, представляющую имя схемы, в которой определен этот тип.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Идентификатор трехкомпонентного имени.<br /><br /> Для столбцов определяемого пользователем типа это свойство содержит строку, представляющую однокомпонентное имя определяемого пользователем типа.|  
  
 Свойство SSPROP_PARAM_UDT_NAME является обязательным. Свойства SSPROP_PARAM_UDT_CATALOGNAME и SSPROP_PARAM_UDT_SCHEMANAME не обязательны. Если какое-либо свойство указывается неправильно, возвращается ошибка DB_E_ERRORSINCOMMAND. Если свойства SSPROP_PARAM_UDT_CATALOGNAME и SSPROP_PARAM_UDT_SCHEMANAME не указаны, то определяемый пользователем тип должен быть определен в той же базе данных и схеме, что и таблица. Если определение определяемого пользователем типа и таблица находятся в разных схемах (но в одной базе данных), то должно быть указано свойство SSPROP_PARAM_UDT_SCHEMANAME. Если определение определяемого пользователем типа находится в другой базе данных, то должны быть указаны свойства SSPROP_PARAM_UDT_CATALOGNAME и SSPROP_PARAM_UDT_SCHEMANAME.  
  
#### <a name="the-dbpropset_sqlservercolumn-property-set"></a>Набор свойств DBPROPSET_SQLSERVERCOLUMN  
 Для поддержки создания таблиц в интерфейсе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ITableDefinition** Native Client добавляет следующие три новых столбца в набор свойств DBPROPSET_SQLSERVERCOLUMN.  
  
|Имя|Описание|Тип|Описание|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|Для столбцов типа DBTYPE_UDT это свойство содержит строку, указывающую имя каталога, в котором определен определяемый пользователем тип.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|Для столбцов типа DBTYPE_UDT это свойство содержит строку, указывающую имя схемы, в которой определен определяемый пользователем тип.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|Для столбцов типа DBTYPE_UDT это свойство содержит строку, указывающую однокомпонентное имя определяемого пользователем типа. Для других типов столбцов это свойство возвращает пустую строку.|  
  
> [!NOTE]  
>  Определяемые пользователем типы не отображаются в наборе строк схемы PROVIDER_TYPES. Все столбцы доступны для чтения и записи.  
  
 ADO будет ссылаться на эти свойства с помощью соответствующей записи в столбце «Описание».  
  
 Свойство SSPROP_COL_UDTNAME является обязательным. Свойства SSPROP_COL_UDT_CATALOGNAME и SSPROP_COL_UDT_SCHEMANAME не обязательны. Если какое-либо из свойств будет указано неправильно, **DB_E_ERRORSINCOMMAND** будет возвращен.  
  
 Если ни свойство SSPROP_PARAM_UDT_CATALOGNAME, ни свойство SSPROP_PARAM_UDT_SCHEMANAME не указаны, то определяемый пользователем тип должен быть определен в той же базе данных и схеме, что и таблица.  
  
 Если определение определяемого пользователем типа и таблица находятся в разных схемах (но в одной базе данных), то должно быть указано свойство SSPROP_COL_UDT_SCHEMANAME.  
  
 Если определение определяемого пользователем типа находится в другой базе данных, то должны быть указаны свойства SSPROP_COL_UDT_CATALOGNAME и SSPROP_COL_UDT_CATALOGNAME.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Добавления и изменения для интерфейсов OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Родной клиент добавляет новые значения или изменения во многие основные интерфейсы OLE DB.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Интерфейс ISSCommandWithParameters  
 Для поддержки UDT через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, Native Client внедряет ряд изменений, включая добавление интерфейса **ISSCommandWithParameters.** Этот новый интерфейс наследует основной интерфейс OLE DB — **ICommandWithParameters**. В дополнение к трем методам, унаследованных от **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, и **SetParameterInfo**; **ISSCommandWithParameters** предоставляет методы **GetParameterProperties** и **SetParameterProperties,** которые используются для обработки конкретных типов данных сервера.  
  
> [!NOTE]  
>  Интерфейс **ISSCommandWithParameters** также задействует возможности новой структуры SSPARAMPROPS.  
  
#### <a name="the-icolumnsrowset-interface"></a>Интерфейс IColumnsRowset  
 В дополнение к интерфейсу **ISSCommandWithParameters,** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client также добавляет новые значения в набор строк, возвращенных из вызова **IColumnsRowset::GetColumnRowset** метод, включая следующие.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Идентификатор имени каталога определяемого пользователем типа.|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Идентификатор имени схемы определяемого пользователем типа.|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Идентификатор имени определяемого пользователем типа.|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Полное имя сборки, которое включает имя типа и все идентификационные данные сборки, необходимые для ссылки на сборку из среды CLR.|  
  
 Если столбец DBCOLUMN_TYPE имеет значение DBTYPE_UDT, то столбец определяемого пользователем типа сервера можно отличить от других двоичных типов, изучив добавленные метаданные определяемого пользователем типа, указанные выше. Если данные частично завершены, то тип сервера является определяемым пользователем типом. Для типов сервера, отличных от определяемых пользователем типов, эти столбцы всегда возвращают значение NULL.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 В драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC Native Client был внесен ряд изменений для поддержки UDT. Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отображает UDT, чтобы SQL_SS_UDT идентификатор типа данных типа s-L, специфичный для драйвера. Столбцы определяемого пользователем типа отображаются как тип SQL_SS_UDT. Если вы сопоставите столбец UDT явно к другому типу в выписке s'L, используя методы **ToString** или **ToXMLString** UDT или через функцию **CAST/CONVERT,** тип столбца в наборе результатов отражает фактический тип, в который был преобразован столбец  
  
### <a name="sqlcolattribute-sqldescribeparam-sqlgetdescfield"></a>SQLColAttribute, SQLDescribeParam, SQLGetDescField  
 Были добавлены четыре новых поля дескриптора для конкретного драйвера, чтобы предоставить дополнительную информацию либо для столбца UDT набора результатов, так и для параметра UDT сохраненной процедуры/параметризованного запроса, который будет получен через функции [S'LColAttribute,](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md) [S'LDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)и [S'LGetDescField.](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
 Это следующие поля дескриптора: SQL_CA_SS_UDT_CATALOG_NAME, SQL_CA_SS_UDT_SCHEMA_NAME, SQL_CA_SS_UDT_TYPE_NAME и SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="sqlcolumns-sqlprocedurecolumns"></a>SQLColumns, SQLProcedureColumns  
 Кроме того, к набору результатов, возвращенному из функций [S'LColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) и [S'LProcedureColumns,](../../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md) добавляются три новых столбца драйвера, чтобы предоставить дополнительную информацию о столбце набора результатов UDT или параметре UDT. Это следующие столбцы: SS_UDT_CATALOG_NAME, SS_UDT_SCHEMA_NAME и SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="supported-conversions"></a>Поддерживаемые преобразования  
 При преобразовании из типов данных SQL в типы данных C типы SQL_C_WCHAR, SQL_C_BINARY и SQL_C_CHAR могут быть преобразованы в SQL_SS_UDT. Однако обратите внимание, что при преобразовании из типов данных SQL_C_WCHAR и SQL_C_CHAR SQL двоичные данные преобразуются в шестнадцатеричную строку.  
  
 При преобразовании из типов данных C в типы данных SQL типы SQL_C_WCHAR, SQL_C_BINARY и SQL_C_CHAR могут быть преобразованы в SQL_SS_UDT. Однако обратите внимание, что при преобразовании из типов данных SQL_C_WCHAR и SQL_C_CHAR SQL двоичные данные преобразуются в шестнадцатеричную строку.  
  
## <a name="see-also"></a>См. также:  
 [Особенности родного клиента сервера S'L](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [ISSCommandWithParameters (OLE DB)](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
