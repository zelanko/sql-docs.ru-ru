---
title: sys. DM _db_objects_disabled_on_compatibility_level_change (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_objects_disabled_on_compatibility_level_change
- dm_db_objects_disabled_on_compatibility_level_change_TSQL
- sys.dm_db_objects_disabled_on_compatibility_level_change
- sys.dm_db_objects_disabled_on_compatibility_level_change_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_objects_disabled_on_compatibility_level_change catalog view
ms.assetid: a5d70064-0330-48b9-b853-01eba50755d0
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 30c3a5d7358e49c1e1762fbb9851066bdaf30871
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68809902"
---
# <a name="spatial-data---sysdm_db_objects_disabled_on_compatibility_level_change"></a>Пространственные данные — sys. DM _db_objects_disabled_on_compatibility_level_change
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Перечисляет индексы и ограничения, которые будут отключены в результате изменения уровня совместимости в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Индексы и ограничения, содержащие материализованные вычисляемые столбцы, в выражениях которых используются пространственные определяемые пользователем типы, будут отключены после обновления или изменения уровня совместимости. Данная функция динамического управления используется для определения влияния изменений уровня совместимости.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sys.dm_db_objects_disabled_on_compatibility_level_change ( compatibility_level )   
```  
  
##  <a name="Arguments"></a> Аргументы  
 *compatibility_level*  
 **целое** число, определяющее уровень совместимости, который вы планируете задать.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**class**|**int**|1 = ограничения<br /><br /> 7 = индексы и кучи|  
|**class_desc**|**nvarchar(60)**|OBJECT или COLUMN для ограничений<br /><br /> INDEX для индексов и куч|  
|**major_id**|**int**|OBJECT ID ограничений<br /><br /> OBJECT ID таблицы, в которой содержатся индексы и кучи.|  
|**minor_id**|**int**|NULL для ограничений<br /><br /> Index_id для индексов и куч|  
|**зависимостей**|**nvarchar(60)**|Описание зависимости, которая вызывает отключение ограничения или индекса. Эти же значения используются также в предупреждениях, возникающих во время обновления. Вот несколько примеров.<br /><br /> space для встроенных<br /><br /> geometry для системы определяемого пользователем типа<br /><br /> geography::Parse для метода системного определяемого пользователем типа|  
  
## <a name="general-remarks"></a>Общие замечания  
 Материализованные вычисляемые столбцы, использующие некоторые встроенные функции, отключаются при изменении уровня совместимости. Кроме того, материализованные вычисляемые столбцы, использующие геометрический или географический метод, отключаются при обновлении базы данных.  
  
### <a name="which-functions-cause-persisted-computed-columns-to-be-disabled"></a>Использование каких функций приводит к отключению материализованных вычисляемых столбцов?  
 При использовании следующих функций в выражении материализованных вычисляемых столбцов происходит отключение индексов и ограничений, которые ссылаются на данные столбцы, в ходе изменения уровня совместимости с 80 на 90.  
  
-   **IsNumeric**  
  
 При использовании следующих функций в выражении материализованных вычисляемых столбцов происходит отключение индексов и ограничений, которые ссылаются на данные столбцы, в ходе изменения уровня совместимости с 100 на 110 или выше.  
  
-   **SOUNDEX**  
  
-   **География:: GeomFromGML**  
  
-   **География:: STGeomFromText**  
  
-   **География:: STLineFromText**  
  
-   **География:: STPolyFromText**  
  
-   **География:: STMPointFromText**  
  
-   **География:: STMLineFromText**  
  
-   **География:: STMPolyFromText**  
  
-   **География:: STGeomCollFromText**  
  
-   **География:: STGeomFromWKB**  
  
-   **География:: STLineFromWKB**  
  
-   **География:: STPolyFromWKB**  
  
-   **География:: STMPointFromWKB**  
  
-   **География:: STMLineFromWKB**  
  
-   **География:: STMPolyFromWKB**  
  
-   **География:: STUnion**  
  
-   **География:: STIntersection**  
  
-   **География:: STDifference**  
  
-   **География:: STSymDifference**  
  
-   **География:: STBuffer**  
  
-   **География:: BufferWithTolerance**  
  
-   **География:: Проанализировать**  
  
-   **География:: Свести**  
  
### <a name="behavior-of-the-disabled-objects"></a>Поведение отключенных объектов  
 **Индексы**  
  
 Если кластеризованный индекс отключен или принудительно задан некластеризованный индекс, возникает следующая ошибка: "Обработчику запросов не удалось создать план, поскольку индекс"%. \*ls "для таблицы или представления"%. \*ls "отключено". Чтобы повторно включить эти объекты, перестройте индексы после обновления, вызвав **инструкцию ALTER INDEX ON... REBUILD**.  
  
 **Кучи**  
  
 При использовании таблицы с отключенной кучей возникает следующая ошибка. Чтобы повторно включить эти объекты, перестройте после обновления, вызвав **инструкцию ALTER INDEX ALL ON... REBUILD**.  
  
```  
// ErrorNumber: 8674  
// ErrorSeverity: EX_USER  
// ErrorFormat: The query processor is unable to produce a plan because the table or view '%.*ls' is disabled.  
// ErrorCause: The table has a disabled heap.   
// ErrorCorrectiveAction: Rebuild the disabled heap to enable it.   
// ErrorInserts: table or view name   
// ErrorOwner: mtintor   
// ErrorFirstProduct: SQL11  
```  
  
 При попытке перестроить кучу во время операции в сети возникает ошибка.  
  
 **Ограничения CHECK и внешние ключи**  
  
 При отключенных проверочных ограничениях и внешних ключах сообщение об ошибке не возникает. Однако ограничения не применяются при изменении строк. Чтобы повторно включить эти объекты, проверьте ограничения после обновления, вызвав **инструкцию ALTER TABLE... ПРОВЕРОЧНОЕ**ОГРАНИЧЕНИЕ.  
  
 **Материализованные вычисленные столбцы**  
  
 При отсутствии возможности отключения отдельного столбца отключается вся таблица посредством отключения кластеризованного индекса или кучи.  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
## <a name="example"></a>Пример  
 В следующем примере показан запрос к **sys. DM _db_objects_disabled_on_compatibility_level_change** для поиска объектов, на которые влияет изменение уровня совместимости до 120.  
  
```sql  
SELECT * FROM sys.dm_db_objects_disabled_on_compatibility_level_change(120);  
GO  
  
```  
  
  
