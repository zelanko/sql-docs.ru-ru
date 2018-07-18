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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4754553f3ceaab83497287f613fa18c5b324c4b3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432633"
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
|**Выберите \* из таблицы** или идентификаторах.|Возвращает все столбцы, которые не являются членами разреженного **column_set**, а также XML-столбец, который содержит значения всех ненулевых столбцов, которые являются членами разреженного **column_set**.|  
|Ссылка на столбец по имени.|На столбец можно ссылаться независимо от состояния разреженности или **column_set** членства.|  
|Доступ **column_set** член столбцов с помощью вычисляемого столбца XML.|Столбцы, являющиеся элементами набора разреженных столбцов **column_set** может осуществляться, выбрав **column_set** по имени и может иметь значения вставляются и обновляются при обновлении XML в **column_set** столбца.<br /><br /> Значение должно соответствовать схеме для **column_set** столбцов.|  
|Получить метаданные для всех столбцов в таблице при помощи SQLColumns с шаблоном поиска столбца NULL или «%» (ODBC). или с помощью набора строк схемы DBSCHEMA_COLUMNS без ограничений столбца (OLE DB).|Возвращает строку для всех столбцов, которые не являются членами **column_set**. Если таблица содержит разреженный **column_set**, строка будет возвращаться для него.<br /><br /> Обратите внимание, что это не возвращает метаданные для столбцов, которые являются членами **column_set**.|  
|Получить метаданные для всех столбцов, независимо от разреженности или вхождения в **column_set**. В этом случае может вернуться очень большое число строк.|Установите для поля дескриптора SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_EXTENDED и вызовите [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Вызовите IDBSchemaRowset::GetRowset для набора строк схемы DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления напрямую.|  
|Получить метаданные только для столбцов, которые являются членами **column_set**. В этом случае может вернуться очень большое число строк.|Установите для поля дескриптора SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET и вызовите SQLColumns (ODBC).<br /><br /> Вызовите IDBSchemaRowset::GetRowset для набора строк схемы DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определение, является ли столбец разреженным.|Обратитесь к столбцу SS_IS_SPARSE результирующего набора SQLColumns (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_SPARSE результирующего набора строк схемы DBSCHEMA_COLUMNS (ODBC).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определить, является ли столбец **column_set**.|Обратитесь к столбцу SS_IS_COLUMN_SET результирующего набора SQLColumns. Или обратитесь к конкретному атрибуту столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CA_SS_IS_COLUMN_SET (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_COLUMN_SET набора строк схемы DBSCHEMA_COLUMNS. Или обратитесь к *dwFlags* возвращаемый IColumnsinfo::GetColumnInfo или DBCOLUMNFLAGS в наборе строк, возвращенных IColumnsRowset::GetColumnsRowset. Для **column_set** столбцы, будет установлен DBCOLUMNFLAGS_SS_ISCOLUMNSET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц без **column_set**.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в поведении нет.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблицы с **column_set**.|**Column_set** импортируется и экспортируется таким же образом, как в XML, то есть как **varbinary(max)** Если привязан как двоичному типу, или как **nvarchar(max)** Если привязаны как **char** или **wchar** типа.<br /><br /> Столбцы, являющиеся элементами набора разреженных столбцов **column_set** не экспортируются как отдельные столбцы, они экспортируются только в значении параметра **column_set**.|  
|**queryout** поведение для BCP.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в обработке столбцов с явно заданными именами нет.<br /><br /> Сценарии, задействующие импорт и экспорт между таблицами с различными схемами, могут потребовать специальной обработки.<br /><br /> Дополнительные сведения о программе BCP см. в подразделе «Поддержка массового копирования (BCP) для разреженных столбцов» далее в данном разделе.|  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиенты низкого уровня вернут метаданные только для столбцов, которые не являются членами разреженного **column_set** SQLColumns и DBSCHMA_COLUMNS. Дополнительные наборы строк схемы OLE DB, представленные в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client не будут доступны, и не будет изменений SQLColumns в ODBC через SQL_SOPT_SS_NAME_SCOPE.  
  
 Клиенты низкого уровня могут обращаться к столбцам, являющимся элементами набора разреженных столбцов **column_set** по имени и **column_set** столбца будет доступен как XML-столбец для [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] клиентов.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Поддержка массового копирования (BCP) для разреженных столбцов  
 Нет изменений в API BCP в ODBC или OLE DB для разреженных столбцов или **column_set** функции.  
  
 Если таблица имеет **column_set**, разреженные столбцы не обрабатываются как отдельные столбцы. Значения всех разреженных столбцов включаются в значение **column_set**, который экспортируется в так же, как XML-столбец; то есть как **varbinary(max)** Если привязан как двоичному типу, или как  **nvarchar(max)** Если привязаны как **char** или **wchar** типа). При импорте **column_set** значение должно соответствовать схеме **column_set**.  
  
 Для **queryout** операций, никак не изменяется, как обрабатываются явно указанным столбцам. **COLUMN_SET** столбцы имеют одинаковое поведение XML-столбцов, и разреженность не имеет значения для обработки именованных разреженных столбцов.  
  
 Тем не менее если **queryout** используется для экспорта и ссылаться на разреженные столбцы, которые являются членами разреженного столбца по имени, не удается осуществить импорт напрямую в таблицу такой же структуры. Это обусловлено тем, программа BCP использует метаданные, согласованные с **выберите \***  операции для импорта и не может сопоставить **column_set** столбцы-члены с этими метаданными. Чтобы импортировать **column_set** столбцы-члены по отдельности, необходимо определить представление для таблицы, который ссылается на нужное **column_set** столбцы, необходимо выполнить операцию импорта, с помощью представления.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
