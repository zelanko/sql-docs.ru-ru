---
title: Поддержка разреженных столбцов в собственном клиенте SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 089c35fd4fffaa2f531dc09b407f1800cc962b92
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533144"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Поддержка разреженных столбцов в собственном клиенте SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает разреженные столбцы. Дополнительные сведения о разреженных столбцах в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], см. в разделе [Использование разреженных столбцов](../../../relational-databases/tables/use-sparse-columns.md) и [использование наборов столбцов](../../../relational-databases/tables/use-column-sets.md).  
  
 Дополнительные сведения о разреженных столбцов поддержки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, см. в разделе [поддерживает разреженные столбцы &#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) и [поддерживает разреженные столбцы &#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md) .  
  
 Сведения о примерах приложений, которые демонстрируют эту функцию, см. в разделе [Образцы программирования для SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Пользовательские сценарии для разреженных столбцов и собственный клиент SQL Server  
 Следующая таблица содержит обычные пользовательские сценарии работы с разреженными столбцами для пользователей собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Сценарий|Поведение|  
|--------------|--------------|  
|**Выберите \* из таблицы** или идентификаторах.|Возвращает все столбцы, которые не являются элементами набора разреженных столбцов **column_set** плюс XML-столбец, содержащий значения ненулевых столбцов, являющихся элементами набора разреженных столбцов **column_set**.|  
|Ссылка на столбец по имени.|На столбец можно ссылаться независимо от состояния разреженности или вхождения в **column_set**.|  
|Доступ к столбцам-элементам **column_set** через вычисляемый XML-столбец.|К столбцам, являющимся элементами **column_set**, можно получить доступ при помощи выборки **column_set** по имени; эти столбцы могут содержать значения, вставленные и обновленные при обновлении XML в столбце **column_set**.<br /><br /> Значение должно соответствовать схеме для столбцов **column_set**.|  
|Получить метаданные для всех столбцов в таблице при помощи SQLColumns с шаблоном поиска столбца NULL или «%» (ODBC). или с помощью набора строк схемы DBSCHEMA_COLUMNS без ограничений столбца (OLE DB).|Возвращает строку для всех столбцов, не входящих в **column_set**. Если таблица содержит разреженный **column_set**, для него будет возвращена строка.<br /><br /> Обратите внимание, что при этом не возвращаются метаданные для столбцов, являющихся элементами **column_set**.|  
|Получение данных для всех столбцов, независимо от разреженности или вхождения в **column_set**. В этом случае может вернуться очень большое число строк.|Установите для поля дескриптора SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_EXTENDED и вызовите [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Вызовите IDBSchemaRowset::GetRowset для набора строк схемы DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления напрямую.|  
|Получение метаданных только для столбцов, являющихся элементами **column_set**. В этом случае может вернуться очень большое число строк.|Установите для поля дескриптора SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET и вызовите SQLColumns (ODBC).<br /><br /> Вызовите IDBSchemaRowset::GetRowset для набора строк схемы DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определение, является ли столбец разреженным.|Обратитесь к столбцу SS_IS_SPARSE результирующего набора SQLColumns (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_SPARSE результирующего набора строк схемы DBSCHEMA_COLUMNS (ODBC).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определить, является ли столбец **column_set**.|Обратитесь к столбцу SS_IS_COLUMN_SET результирующего набора SQLColumns. Или обратитесь к конкретному атрибуту столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CA_SS_IS_COLUMN_SET (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_COLUMN_SET набора строк схемы DBSCHEMA_COLUMNS. Или обратитесь к *dwFlags* возвращаемый IColumnsinfo::GetColumnInfo или DBCOLUMNFLAGS в наборе строк, возвращенных IColumnsRowset::GetColumnsRowset. Для **column_set** столбцы, будет установлен DBCOLUMNFLAGS_SS_ISCOLUMNSET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц без **column_set**.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в поведении нет.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц с **column_set**.|**Column_set** импортируется и экспортируется таким же образом, как в XML, то есть как **varbinary(max)** Если привязан как двоичному типу, или как **nvarchar(max)** Если привязаны как **char** или **wchar** типа.<br /><br /> Столбцы, являющиеся элементами набора разреженных столбцов **column_set**, не экспортируются как отдельные столбцы. Они экспортируются только в составе значения столбца **column_set**.|  
|**queryout** поведение для BCP.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в обработке столбцов с явно заданными именами нет.<br /><br /> Сценарии, задействующие импорт и экспорт между таблицами с различными схемами, могут потребовать специальной обработки.<br /><br /> Дополнительные сведения о программе BCP см. в подразделе «Поддержка массового копирования (BCP) для разреженных столбцов» далее в данном разделе.|  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиенты низкого уровня вернут метаданные только для столбцов, которые не являются элементами набора разреженных столбцов **column_set** для SQLColumns и DBSCHMA_COLUMNS. Дополнительные наборы строк схемы OLE DB, представленные в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client не будут доступны, и не будет изменений SQLColumns в ODBC через SQL_SOPT_SS_NAME_SCOPE.  
  
 Клиенты низкого уровня могут получить доступ к столбцам, являющимся элементами набора разреженных столбцов **column_set**, по имени. Столбец **column_set** будет доступен как XML-столбец для клиентов [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Поддержка массового копирования (BCP) для разреженных столбцов  
 Нет изменений в API BCP в ODBC или OLE DB для разреженных столбцов или **column_set** функции.  
  
 Если таблица содержит **column_set**, то разреженные столбцы не обрабатываются как отдельные столбцы. Значения всех разреженных столбцов включаются в значение **column_set**, который экспортируется в так же, как XML-столбец; то есть как **varbinary(max)** Если привязан как двоичному типу, или как  **nvarchar(max)** Если привязаны как **char** или **wchar** типа). При импорте **column_set** значение должно соответствовать схеме **column_set**.  
  
 Для операций **queryout** нет изменений в способе обработки столбцов, на которые имеются явные ссылки. Поведение столбцов **column_set** совпадает с поведением XML-столбцов, и разреженность не имеет значения для обработки именованных разреженных столбцов.  
  
 Однако, если **queryout** используется для экспорта и пользователь ссылается по имени на разреженные столбцы, являющиеся элементами набора разреженных столбцов, нельзя осуществить импорт напрямую в таблицу такой же структуры. Это обусловлено тем, что программа BCP использует для импорта метаданные, согласованные с операцией **select \***, и не может сопоставить столбцы-элементы **column_set** с этими метаданными. Для отдельного импорта каждого столбца, входящего в набор разреженных столбцов **column_set**, необходимо определить представление для таблицы, которая ссылается на необходимые столбцы набора **column_set**, и выполнить операцию импорта с помощью этого представления.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
