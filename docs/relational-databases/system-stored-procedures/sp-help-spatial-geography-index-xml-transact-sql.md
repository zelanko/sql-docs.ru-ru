---
title: sp_help_spatial_geography_index_xml (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7d25c8d57608357530e9344a41d23771d198ed23
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717272"
---
# <a name="sp_help_spatial_geography_index_xml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает имя и значение для указанного набора свойств пространственного индекса **Geography** . Можно задать возврат основного набора свойств или всех свойств индекса.  
  
 Результаты возвращаются во фрагменте XML, который отображает имена и значения выбранных свойств.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 См. раздел [аргументы и свойства хранимых процедур пространственного индекса](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Свойства  
 См. раздел [аргументы и свойства хранимых процедур пространственного индекса](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Разрешения  
 Пользователю должна быть назначена роль PUBLIC для получения доступа к процедуре. Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Примечания  
 Свойства, которые содержат значения NULL, не включаются в набор возвращаемых значений.  
  
## <a name="example"></a>Пример  
 В следующем примере используется `sp_help_spatial_geography_index_xml` для исследования пространственного индекса **SIndx_SpatialTable_geography_col2** , определенного в таблице **geography_col** для данного примера запроса в ** \@ QS**. В этом примере основные свойства указанного индекса возвращаются в XML-фрагменте, в котором отображаются имя и значение выбранных свойств.  
  
 Затем в результирующем наборе выполняется [запрос XQuery](../../xquery/xquery-basics.md) , возвращающий определенное свойство.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Подобно [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md), эта хранимая процедура предоставляет более простой программный доступ к свойствам пространственного индекса **Geography** и сообщает РЕЗУЛЬТИРУЮЩИЙ набор в формате XML.  
  
 Ограничивающий прямоугольник **географии** — это вся земля.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [SQL Server &#40;пространственных данных&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Основы XQuery](../../xquery/xquery-basics.md)   
 [Справочник по языку XQuery](../../xquery/xquery-language-reference-sql-server.md)  
  
  
