---
title: "sp_help_spatial_geometry_index_xml (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index_xml_TSQL
- sp_help_spatial_geometry_index_xml
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geometry_index_xml procedure
ms.assetid: 9668ae6d-9ed5-418e-bb9a-9e7b66f7dd16
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ff25ea117e7a97e733cade78d6d4620684a7fc7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpspatialgeometryindexxml-transact-sql"></a>sp_help_spatial_geometry_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает имена и значения для указанного набора свойств о **geometry** пространственного индекса. Можно задать возврат основного набора свойств или всех свойств индекса.  
  
 Результаты возвращаются во фрагменте XML, который отображает имена и значения выбранных свойств.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ]'{ 0 | 1 }]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 В разделе [аргументов и свойств пространственного индекса хранимые процедуры](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Свойства  
 В разделе [аргументов и свойств пространственного индекса хранимые процедуры](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен быть членом **открытый** роли. Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Замечания  
 Свойства, которые содержат значения NULL, не включаются в набор возвращаемых значений XML.  
  
## <a name="example"></a>Пример  
 В следующем примере используется `sp_help_spatial_geometry_index_xml` для анализа пространственного индекса **SIndx_SpatialTable_geometry_col2** определен в таблице **geometry_col** для определенного образца запроса в  **@qs** . В этом примере основные свойства указанного индекса возвращаются в XML-фрагменте, в котором отображаются имя и значение выбранных свойств.  
  
 [XQuery](../../xquery/xquery-basics.md) запустите на результирующий набор возвращается определенное свойство.  
  
```  
DECLARE @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
DECLARE @x xml;  
EXEC sp_help_spatial_geometry_index_xml 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs, @x output;  
SELECT @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Аналогично [sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md), эта хранимая процедура обеспечивает более простой программный доступ к свойствам пространственного индекса и возвращает результирующий набор в формате XML.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также:  
 [Аргументы и свойства пространственного индекса хранимых процедур](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)   
 [Хранимые процедуры пространственного индекса](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Основы языка XQuery](../../xquery/xquery-basics.md)   
 [Справочник по языку XQuery](../../xquery/xquery-language-reference-sql-server.md)  
  
  
