---
title: 'Изменения в формат хранения для типов xs: DateTime, xs: Date и xs: Time | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xs:date
- xs:time
- storage format
- DateTime
ms.assetid: b9f758df-030c-4aec-8ade-1bf904aa2c61
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f631783aad92757edd4faae41cd43c06c431887
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096607"
---
# <a name="changes-to-the-storage-format-for-types-xsdatetime-xsdate-and-xstime"></a>Изменение формата хранения для типов xs:dateTime, xs:date и xs:time
  Правило XMLDATETIME определяет, содержат ли базы данных типизированные XML-данные, которые станут недопустимыми после обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Формат хранения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для типов xs: DateTime, xs: Date и xs: Time был изменен для поддержки значения с или без сведений о часовом поясе и разрешить сохранение часового пояса.  
  
 Если коллекция XML-схем ссылается на один из таких типов, XML-индексы на всех столбцах, связанных с коллекцией, будут выключены до обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Запросы к ним с помощью инструкций SELECT и запросов XQUERIES будут возможны, но XML-индекс при этом использоваться не будет. Отрицательное значение года вызовет ошибку времени выполнения.  
  
 Кроме того, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает значения с отрицательным годом.  
  
 Правило XMLDATETIME проверяет, ссылается ли какая-либо коллекция XML-схем на затронутые типы и имеются ли XML-столбцы, типизированные по таким коллекциям.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если правило XMLDATETIME подтверждает, что имеются XML-столбцы, типизированные в соответствии с коллекцией схем, ссылающейся на типы xs:date, xs:time или xs:dateTime, необходимо предварительно проверить, имеются ли в наборе данных значения с отрицательным годом. При наличии таких значений перестроить XML-индексы после обновления не удастся.  
  
 Следующий запрос выполняет поиск коллекций XML-схем, ссылающихся на затронутые типы, а также типизированных XML-столбцов. Это позволит определить, имеются ли экземпляры с отрицательными значениями года.  
  
```sql
CREATE PROCEDURE DateTimeInvestigation(@withdata bit)  
-- @withdata = 0: only get the affected meta data information  
-- @withdata = 1: get the affected meta data and instance information  
AS  
BEGIN  
-- First get XML containing all schema collections containing affected element and attributes  
-- components (model groups?)   
-- and columns that are affected by the schema collections.   
CREATE table #_dt_collector(x xml);   
;with dttypes as  
  (SELECT * FROM sys.xml_schema_components   
   where base_xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
      )   
   union all  
   SELECT * FROM sys.xml_schema_components  
   where xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
       or kind='N' or kind='Z')   
   ),   
dtplaced as  
  (SELECT scp.*   
   FROM sys.xml_schema_component_placements scp   
   JOIN dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
  )   
insert into #_dt_collector SELECT x FROM (SELECT  
  xsc.xml_collection_id as "@collid"  
, s.name as "@schema"  
, xscol.name as "@name"  
, count(xsc.xml_component_id) as "@affected_elems_and_attrs"  
, (SELECT S.Name as "@schema", T.Name as "@table"  
        , C.Name as "@column"   
   FROM sys.columns C   
   JOIN sys.tables T ON C.object_id = T.object_id  
   JOIN sys.schemas S ON S.schema_id = T.schema_id  
   WHERE C.xml_collection_id = xsc.xml_collection_id  
   FOR XML PATH('Columns'), TYPE  
  )   
FROM sys.xml_schema_components xsc  
JOIN dtplaced on xsc.xml_component_id=dtplaced.xml_component_id  
JOIN sys.xml_schema_collections xscol on xsc.xml_collection_id =xscol.xml_collection_id  
JOIN sys.schemas s on xscol.schema_id=s.schema_id  
group by xsc.xml_collection_id, s.name, xscol.name  
FOR XML PATH('XML_Schema_Collections'), TYPE) as T(x);   
if (@withdata = 0)    
  BEGIN  
  SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
  drop table #_dt_collector;   
  return;   
  END;   
-- Declare cursor to find all columns bound to the schema collections  
DECLARE C CURSOR FOR  
SELECT S.Name, T.Name, C.Name   
FROM sys.columns C   
JOIN sys.tables T ON C.object_id = T.object_id  
JOIN sys.schemas S ON S.schema_id = T.schema_id  
WHERE C.xml_collection_id  
IN (SELECT distinct xsc.xml_collection_id  
    FROM sys.xml_schema_components xsc  
    JOIN (SELECT scp.*   
          FROM sys.xml_schema_component_placements scp   
          JOIN (SELECT * FROM sys.xml_schema_components   
                where base_xml_component_id    
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                   )   
                union all  
                SELECT * FROM sys.xml_schema_components  
                where xml_component_id   
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                    or kind='N' or kind='Z')   
               ) dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
          ) dtplaced on xsc.xml_component_id=dtplaced.xml_component_id);   
DECLARE @SchemaName nvarchar(max);   
DECLARE @TableName nvarchar(max);   
DECLARE @ColumnName nvarchar(max);   
DECLARE @strSQL nvarchar(MAX);   
OPEN C;   
FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
WHILE (@@FETCH_STATUS = 0)   
BEGIN  
      SET @strSQL = 'INSERT INTO #_dt_collector SELECT x FROM ( ';   
      SET @strSQL = @strSQL +    
                    'SELECT ''' + @SchemaName + '.' + @TableName + '.' + @ColumnName   
                  + ''' as "@Column", ';   
      SET @strSQL = @strSQL +    
      'sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)])'', ''bigint'')) as "@dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)])'', ''bigint'')) as "@date_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_date_elements"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)  
                      where $v instance of xs:dateTime?   
                      return 1)'', ''bigint'')) as "@dT_attributes"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:dateTime?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_dt_attributes"  
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      return 1)'', ''bigint'')) as "@date_attributes"   
     , sum('+ @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_date_attributes"'  
      + ' FROM ' + @SchemaName + '.' + @TableName  
      + ' FOR XML PATH(''data''), type) T(x)';   
      --SELECT @strSQL;   
      EXEC sp_executesql @strSQL;   
      FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
END;   
CLOSE C;   
DEALLOCATE C;   
SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
drop table #_dt_collector;   
END;   
go  
-- Get the dependent columns per affected XML Schema Collection and the  
-- number of affected values  
EXECUTE DateTimeInvestigation 1;   
```  
  
 Если найдены отрицательные значения года, имеется несколько решений:  
  
-   удалить эти строки;  
  
-   обновить эти значения;  
  
-   очистить весь XML-столбец;  
  
-   ввести заново XML-столбец с коллекцией схем, не использующей типы xs:date и xs:dateTime (воспользуйтесь, например, типом xs:string).  
  
 После решения проблемы, связанной с отрицательными значениями года, можно произвести обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Для использования XML-индексов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] необходимо после обновления перестроить XML-индексы или заново ввести все XML-столбцы, использующие типы xs:date, xs:time или xs:dateTime.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядра СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
