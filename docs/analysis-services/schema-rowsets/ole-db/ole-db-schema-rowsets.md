---
title: "Наборы строк схемы OLE DB | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [OLE DB]
- schema rowsets [Analysis Services], OLE DB
- OLE DB schema rowsets
- rowsets [Analysis Services], OLE DB
ms.assetid: ca2ee87a-ba04-4501-9125-33934c58ab31
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 59d17cb1345f7ba32a2cbaac27f5ec002aadfa40
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="ole-db-schema-rowsets"></a>Наборы строк схемы OLE DB
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Поддерживаются следующие наборы строк схемы OLE DB [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика. Используйте **DISCOVER_ENUMERATORS** набора строк с [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод для проверки, поддерживает ли конкретный поставщик источника данных набор строк.  
  
 Подробные сведения об этих наборах строк также можно найти путем поиска см. в разделе «Наборы строк схемы» в части Справочник программиста OLE DB в библиотеке MSDN® на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] веб-сайта.  
  
 В следующей таблице приведено описание этого набора строк схемы.  
  
|Набор строк|Description|  
|------------|-----------------|  
|**DBSCHEMA_ASSERTIONS**|Обозначает предположения, которые определены в каталоге и принадлежат какому-то конкретному пользователю.|  
|[Набор строк DBSCHEMA_CATALOGS](../../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md) <sup>1</sup>|Определяет физические атрибуты, связанные с каталогами, доступными из системы управления базами данных (СУБД). Для некоторых систем, таких как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access, может быть предусмотрен только один каталог. Что касается [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], этот набор строк перечисляет все каталоги (базы данных), определенные в базе данных system.|  
|**DBSCHEMA_CHARACTER_SETS**|Указывает, какие кодировки определены в каталоге и доступны для данного пользователя.|  
|**DBSCHEMA_CHECK_CONSTRAINTS**|Указывает проверочные ограничения, которые определены в каталоге и принадлежат данному пользователю.|  
|**DBSCHEMA_CHECK_CONSTRAINTS_BY_TABLE**|Указывает проверочные ограничения для данной таблицы, определенной в каталоге, который принадлежит данному пользователю.|  
|**DBSCHEMA_COLLATIONS**|Указывает символьные параметры сортировки, которые определены в каталоге и доступны для данного пользователя.|  
|**DBSCHEMA_COLUMN_DOMAIN_USAGE**|Указывает столбцы, определенные в каталоге, которые зависят от домена, определенного в каталоге и принадлежащего данному пользователю.|  
|**DBSCHEMA_COLUMN_PRIVILEGES**|Указывает права доступа к столбцам таблиц, которые определены в каталоге и доступны или могут быть предоставлены данным пользователем.|  
|[Набор строк DBSCHEMA_COLUMNS](../../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md) <sup>1</sup>|Предоставляет сведения обо всех столбцах, удовлетворяющих указанному критерию ограничения.|  
|**DBSCHEMA_CONSTRAINT_COLUMN_USAGE**|Указывает столбцы, используемые в ссылочных ограничениях, ограничениях уникальности, проверочных ограничениях и утверждениях, определенные в каталоге и принадлежащие данному пользователю.|  
|**DBSCHEMA_CONSTRAINT_TABLE_USAGE**|Указывает таблицы, которые используются в ссылочных ограничениях, ограничениях уникальности, проверочных ограничениях и утверждениях и которые определены в каталоге и принадлежат данному пользователю.|  
|**DBSCHEMA_FOREIGN_KEYS**|Указывает внешние ключевые столбцы, определенные в каталоге данным пользователем. Этот набор строк схемы построен на основе нескольких представлений схемы ISO для упрощения работы программиста, не использующего язык SQL. Если поддерживается, в наборе строк схемы должен быть синхронизирован со связанными представлениями ISO (**REFERENTIAL_CONSTRAINTS** и **CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_INDEXES**|Указывает индексы, которые определены в каталоге и принадлежат данному пользователю.|  
|**DBSCHEMA_KEY_COLUMN_USAGE**|Указывает столбцы, которые определены в каталоге и на которые данным пользователем наложены ограничения в виде ключей.|  
|**НАБОРУ СТРОК DBSCHEMA_PRIMARY_KEYS**|Указывает первичные ключевые столбцы, которые определены в каталоге данным пользователем. Этот набор строк схемы построен на основе представления схемы ISO для упрощения работы программиста, не использующего язык SQL. Если поддерживается, в наборе строк схемы должен быть синхронизирован со связанным представлением ISO (**CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_PROCEDURE_COLUMNS**|Возвращает информацию о столбцах наборов строк, возвращаемых процедурами.|  
|**DBSCHEMA_PROCEDURE_PARAMETERS**|Возвращает информацию о параметрах и кодах возврата процедур.|  
|**DBSCHEMA_PROCEDURES**|Указывает процедуры, которые определены в каталоге и принадлежат данному пользователю. Это — модуль OLE DB.|  
|[Набор строк DBSCHEMA_PROVIDER_TYPES](../../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md) <sup>1</sup>|Показывает (базовые) типы данных, поддерживаемые поставщиком данных.|  
|**DBSCHEMA_REFERENTIAL_CONSTRAINTS**|Указывает ссылочные ограничения, которые определены в каталоге и принадлежат данному пользователю.|  
|**DBSCHEMA_SCHEMATA**|Указывает схемы, которые принадлежат данному пользователю.|  
|**DBSCHEMA_SQL_LANGUAGES**|Указывает уровни согласованности, параметры и диалекты, поддерживаемые данными обработки реализации SQL, которые определены в каталоге.|  
|**DBSCHEMA_STATISTICS**|Указывает статистические данные, которые определены в каталоге и принадлежат данному пользователю.<br /><br /> Эта таблица не связана с **TABLE_STATISTICS** набора строк.|  
|**DBSCHEMA_TABLE_CONSTRAINTS**|Указывает ограничения таблицы, которые определены в каталоге и принадлежат данному пользователю.|  
|**DBSCHEMA_TABLE_PRIVILEGES**|Указывает права доступа к таблицам, которые определены в каталоге и доступны данному пользователю или предоставлены им.|  
|**DBSCHEMA_TABLE_STATISTICS**|Описывает доступный набор статистических данных, относящийся к таблицам в поставщике.<br /><br /> Этот набор строк не относится к **СТАТИСТИКИ** набора строк.|  
|[Набор строк DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md) <sup>1</sup>|Определяет группы мер и измерения, представленные в виде таблиц в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|**DBSCHEMA_TABLES_INFO** <sup>1</sup>|Указывает таблицы (включая представления), которые определены в каталоге и доступны данному пользователю.|  
|**DBSCHEMA_TRANSLATIONS**|Указывает преобразования символов, которые определены в каталоге и доступны данному пользователю.|  
|**DBSCHEMA_TRUSTEE**|Перечисляет доверенные лица для источника данных.|  
|**DBSCHEMA_USAGE_PRIVILEGES**|Идентифицирует **использование** прав на объекты, которые определены в каталоге и доступны или предоставлены данным пользователем.|  
|**DBSCHEMA_VIEW_COLUMN_USAGE**|Определяет представления, которые заданы в каталоге и доступны для данного пользователя.|  
|**DBSCHEMA_VIEW_TABLE_USAGE**|Указывает таблицы, от которых зависят рассматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю.|  
|**DBSCHEMA_VIEWS**|Определяет представления, которые заданы в каталоге и доступны для данного пользователя.|  
  
 <sup>1</sup> указывает наборы строк схемы поддерживаются поставщиком источника данных MSOLAP для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика XML для Аналитики.  
  
## <a name="see-also"></a>См. также:  
 [Набор строк DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)   
 [Наборы строк схемы служб Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
