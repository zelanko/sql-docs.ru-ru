---
title: Поддержка sparse столбцов в s'L Родной клиент
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 958424a4710b76e7e09ae15e10b612630f09eee3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303793"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Поддержка разреженных столбцов в собственном клиенте SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает разреженные столбцы. Дополнительные сведения о разреженных столбцах в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]см. в статьях [Использование разреженных столбцов](../../../relational-databases/tables/use-sparse-columns.md) и [Использование наборов столбцов](../../../relational-databases/tables/use-column-sets.md).  
  
 Для получения дополнительной информации о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] разреженной поддержке столбцов в Native Client см. [Sparse Columns Support &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) и [Sparse Columns Support &#40;OLE DB&#41;. ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md)  
  
 Сведения о примерах приложений, которые демонстрируют эту функцию, см. в разделе [Образцы программирования для SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Пользовательские сценарии для разреженных столбцов и собственный клиент SQL Server  
 Следующая таблица содержит обычные пользовательские сценарии работы с разреженными столбцами для пользователей собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Сценарий|Поведение|  
|--------------|--------------|  
|**выберите \* из таблицы** или IOpenRowset::OpenRowset.|Возвращает все столбцы, которые не являются элементами набора разреженных столбцов **column_set** плюс XML-столбец, содержащий значения ненулевых столбцов, являющихся элементами набора разреженных столбцов **column_set**.|  
|Ссылка на столбец по имени.|На столбец можно ссылаться независимо от состояния разреженности или вхождения в **column_set**.|  
|Доступ к столбцам-элементам **column_set** через вычисляемый XML-столбец.|К столбцам, являющимся элементами **column_set**, можно получить доступ при помощи выборки **column_set** по имени; эти столбцы могут содержать значения, вставленные и обновленные при обновлении XML в столбце **column_set**.<br /><br /> Значение должно соответствовать схеме для столбцов **column_set**.|  
|Извлекать метаданные для всех столбцов в таблице через S'LКолонки с шаблоном поиска столбцов NULL или '%' (ODBC); или через DBSCHEMA_COLUMNS схему строки без ограничений столбца (OLE DB).|Возвращает строку для всех столбцов, не входящих в **column_set**. Если таблица содержит разреженный **column_set**, для него будет возвращена строка.<br /><br /> Обратите внимание, что при этом не возвращаются метаданные для столбцов, являющихся элементами **column_set**.|  
|Получение данных для всех столбцов, независимо от разреженности или вхождения в **column_set**. В этом случае может вернуться очень большое число строк.|Установите поле дескриптора SQL_SOPT_SS_NAME_SCOPE, чтобы SQL_SS_NAME_SCOPE_EXTENDED и [вызовs S'LColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Звоните idBSchemaRowset::GetRowset для DBSCHEMA_COLUMNS_EXTENDED схемы rowset (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может непосредственно запрашивать системные представления.|  
|Получение метаданных только для столбцов, являющихся элементами **column_set**. В этом случае может вернуться очень большое число строк.|Установите поле дескриптора SQL_SOPT_SS_NAME_SCOPE, чтобы SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET и вызовs S'LColumns (ODBC).<br /><br /> Звоните idBSchemaRowset::GetRowset для DBSCHEMA_SPARSE_COLUMN_SET схемы rowset (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определение, является ли столбец разреженным.|Проконсультируйтесь с SS_IS_SPARSE колонкой набора результатов S'LColumns (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_SPARSE результирующего набора строк схемы DBSCHEMA_COLUMNS (ODBC).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определение, является ли столбец элементом **column_set**.|Проконсультируйтесь с SS_IS_COLUMN_SET столбцов набора результатов S'LColumns. Или обратитесь к конкретному атрибуту столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CA_SS_IS_COLUMN_SET (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_COLUMN_SET набора строк схемы DBSCHEMA_COLUMNS. Или просмотрите *dwFlags*, возвращенный IColumnsinfo::GetColumnInfo или DBCOLUMNFLAGS в наборе строк, возвращаемом IColumnsRowset::GetColumnsRowset. Для **column_set** столбцов будут установлены DBCOLUMNFLAGS_SS_ISCOLUMNSET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц без **column_set**.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в поведении нет.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц с **column_set**.|**column_set** импортируется и экспортируется так же, как XML; то есть **varbinary(max)**, если он привязан как двоичный тип, или как **nvarchar(max)**, если он привязан как тип **char** или **типа wchar**.<br /><br /> Столбцы, являющиеся элементами набора разреженных столбцов **column_set**, не экспортируются как отдельные столбцы. Они экспортируются только в составе значения столбца **column_set**.|  
|Поведение **queryout** для программы BCP.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в обработке столбцов с явно заданными именами нет.<br /><br /> Сценарии, задействующие импорт и экспорт между таблицами с различными схемами, могут потребовать специальной обработки.<br /><br /> Дополнительные сведения о программе BCP см. в подразделе «Поддержка массового копирования (BCP) для разреженных столбцов» далее в данном разделе.|  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиенты низкого уровня вернут метаданные только для столбцов, которые не являются элементами набора разреженных столбцов **column_set** для SQLColumns и DBSCHMA_COLUMNS. Дополнительные схемы OL DB, [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] представленные в Native Client, не будут доступны, равно как и модификации s'LColumns в ODBC через SQL_SOPT_SS_NAME_SCOPE.  
  
 Клиенты низкого уровня могут получить доступ к столбцам, являющимся элементами набора разреженных столбцов **column_set**, по имени. Столбец **column_set** будет доступен как XML-столбец для клиентов [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Поддержка массового копирования (BCP) для разреженных столбцов  
 Нет никаких изменений в API BCP ни в ODBC, ни в OLE DB для разреженных столбцов или **column_set** функций.  
  
 Если таблица содержит **column_set**, то разреженные столбцы не обрабатываются как отдельные столбцы. Значения всех разреженных столбцов включаются в значение столбца **column_set**, который экспортируется таким же способом, как XML-столбец, то есть как **varbinary(max)**, если привязан как двоичному типу, или как **nvarchar(max)**, если привязан тип **char** или **wchar**). При импорте значение **column_set** должно соответствовать схеме **column_set**.  
  
 Для операций **queryout** нет изменений в способе обработки столбцов, на которые имеются явные ссылки. Поведение столбцов **column_set** совпадает с поведением XML-столбцов, и разреженность не имеет значения для обработки именованных разреженных столбцов.  
  
 Однако, если **queryout** используется для экспорта и пользователь ссылается по имени на разреженные столбцы, являющиеся элементами набора разреженных столбцов, нельзя осуществить импорт напрямую в таблицу такой же структуры. Это связано с тем, что BCP использует метаданные, соответствующие **операции выбора &#42;** для импорта, и не может сопоставить **column_set** столбцов-членов с этими метаданными. Для отдельного импорта каждого столбца, входящего в набор разреженных столбцов **column_set**, необходимо определить представление для таблицы, которая ссылается на необходимые столбцы набора **column_set**, и выполнить операцию импорта с помощью этого представления.  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
