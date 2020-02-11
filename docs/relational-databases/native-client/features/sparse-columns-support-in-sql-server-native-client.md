---
title: Поддержка разреженных столбцов в SQL Native Client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0271b8e07a6e9ea9b797427a66df097e1114cad4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75247418"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Поддержка разреженных столбцов в собственном клиенте SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает разреженные столбцы. Дополнительные сведения о разреженных столбцах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]в см. в разделе [Использование разреженных столбцов](../../../relational-databases/tables/use-sparse-columns.md) и [Использование наборов столбцов](../../../relational-databases/tables/use-column-sets.md).  
  
 Дополнительные сведения о поддержке разреженных столбцов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственном клиенте см. в разделе [Поддержка разреженных столбцов &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) и [разреженные столбцы поддерживают &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md).  
  
 Сведения о примерах приложений, которые демонстрируют эту функцию, см. в разделе [Образцы программирования для SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Пользовательские сценарии для разреженных столбцов и собственный клиент SQL Server  
 Следующая таблица содержит обычные пользовательские сценарии работы с разреженными столбцами для пользователей собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Сценарий|Поведение|  
|--------------|--------------|  
|**выберите \* из таблицы** или IOpenRowset:: OPENROWSET.|Возвращает все столбцы, которые не являются элементами набора разреженных столбцов **column_set** плюс XML-столбец, содержащий значения ненулевых столбцов, являющихся элементами набора разреженных столбцов **column_set**.|  
|Ссылка на столбец по имени.|На столбец можно ссылаться независимо от состояния разреженности или вхождения в **column_set**.|  
|Доступ к столбцам-элементам **column_set** через вычисляемый XML-столбец.|К столбцам, являющимся элементами **column_set**, можно получить доступ при помощи выборки **column_set** по имени; эти столбцы могут содержать значения, вставленные и обновленные при обновлении XML в столбце **column_set**.<br /><br /> Значение должно соответствовать схеме для столбцов **column_set**.|  
|Получение метаданных для всех столбцов в таблице с помощью SQLColumns с шаблоном поиска столбца NULL или "%" (ODBC); или с помощью набора строк схемы DBSCHEMA_COLUMNS без ограничений по столбцам (OLE DB).|Возвращает строку для всех столбцов, не входящих в **column_set**. Если таблица содержит разреженный **column_set**, для него будет возвращена строка.<br /><br /> Обратите внимание, что при этом не возвращаются метаданные для столбцов, являющихся элементами **column_set**.|  
|Получение данных для всех столбцов, независимо от разреженности или вхождения в **column_set**. В этом случае может вернуться очень большое число строк.|Задайте для поля дескриптор SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_EXTENDED и вызовите [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Вызовите метод IDBSchemaRowset:: GetSchema для набора строк схемы DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может непосредственно запрашивать системные представления.|  
|Получение метаданных только для столбцов, являющихся элементами **column_set**. В этом случае может вернуться очень большое число строк.|Задайте для поля дескриптор SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET и вызовите SQLColumns (ODBC).<br /><br /> Вызовите метод IDBSchemaRowset:: GetSchema для набора строк схемы DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определение, является ли столбец разреженным.|Просмотрите столбец SS_IS_SPARSE результирующего набора SQLColumns (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_SPARSE результирующего набора строк схемы DBSCHEMA_COLUMNS (ODBC).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Определить, является ли столбец **column_setом**.|Просмотрите столбец SS_IS_COLUMN_SET результирующего набора SQLColumns. Или обратитесь к конкретному атрибуту столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CA_SS_IS_COLUMN_SET (ODBC).<br /><br /> Обратитесь к столбцу SS_IS_COLUMN_SET набора строк схемы DBSCHEMA_COLUMNS. Или просмотрите *dwFlags* , возвращенный IColumnsinfo:: GETCOLUMNINFO или DBCOLUMNFLAGS в наборе строк, возвращаемом IColumnsRowset:: жетколумнсровсет. Для **column_set** столбцов будет задано DBCOLUMNFLAGS_SS_ISCOLUMNSET (OLE DB).<br /><br /> Этот сценарий невозможен в приложении, которое использует собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранней версии, чем [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Однако такое приложение может запрашивать системные представления.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц без **column_set**.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в поведении нет.|  
|Импорт и экспорт разреженных столбцов программой BCP для таблиц с **column_set**.|**Column_set** импортируется и экспортируется так же, как XML; то есть AS **varbinary (max)** , если он привязан как двоичный тип, или **как nvarchar (max)** , если он привязан как тип **char** или **WCHAR** .<br /><br /> Столбцы, являющиеся элементами набора разреженных столбцов **column_set**, не экспортируются как отдельные столбцы. Они экспортируются только в составе значения столбца **column_set**.|  
|поведение **запроса** для bcp.|Отличий от предыдущих версий собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в обработке столбцов с явно заданными именами нет.<br /><br /> Сценарии, задействующие импорт и экспорт между таблицами с различными схемами, могут потребовать специальной обработки.<br /><br /> Дополнительные сведения о программе BCP см. в подразделе «Поддержка массового копирования (BCP) для разреженных столбцов» далее в данном разделе.|  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиенты низкого уровня вернут метаданные только для столбцов, которые не являются элементами набора разреженных столбцов **column_set** для SQLColumns и DBSCHMA_COLUMNS. Дополнительные OLE DB наборы строк схемы, появившиеся [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] в собственном клиенте, будут недоступны, и изменения в SQLCOLUMNS в ODBC с помощью SQL_SOPT_SS_NAME_SCOPE не будут.  
  
 Клиенты низкого уровня могут получить доступ к столбцам, являющимся элементами набора разреженных столбцов **column_set**, по имени. Столбец **column_set** будет доступен как XML-столбец для клиентов [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Поддержка массового копирования (BCP) для разреженных столбцов  
 В ODBC или OLE DB для разреженных столбцов или **column_set** функций не существует изменений в API BCP.  
  
 Если таблица содержит **column_set**, то разреженные столбцы не обрабатываются как отдельные столбцы. Значения всех разреженных столбцов включаются в значение **column_set**, которое экспортируется так же, как и XML-столбец; то есть AS **varbinary (max)** , если он привязан как двоичный тип, или **как nvarchar (max)** , если он привязан как тип **char** или **WCHAR** ). При импорте значение **column_set** должно соответствовать схеме **column_set**.  
  
 Для операций **queryout** нет изменений в способе обработки столбцов, на которые имеются явные ссылки. **column_set** столбцы имеют то же поведение, что и XML-столбцы, и разреженность не влияет на обработку именованных разреженных столбцов.  
  
 Однако, если **queryout** используется для экспорта и пользователь ссылается по имени на разреженные столбцы, являющиеся элементами набора разреженных столбцов, нельзя осуществить импорт напрямую в таблицу такой же структуры. Это происходит потому, что BCP использует метаданные, согласованные с операцией **select &#42;** для импорта и не может сопоставлять столбцы **column_set** элементов с этими метаданными. Для отдельного импорта каждого столбца, входящего в набор разреженных столбцов **column_set**, необходимо определить представление для таблицы, которая ссылается на необходимые столбцы набора **column_set**, и выполнить операцию импорта с помощью этого представления.  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
