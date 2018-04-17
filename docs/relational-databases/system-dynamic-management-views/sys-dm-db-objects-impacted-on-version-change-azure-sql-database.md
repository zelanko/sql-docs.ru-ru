---
title: sys.dm_db_objects_impacted_on_version_change (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_objects_impacted_on_version_change_TSQL
- dm_db_objects_impacted_on_version_change
- dm_db_objects_impacted_on_version_change_TSQL
- sys.dm_db_objects_impacted_on_version_change
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_objects_impacted_on_version_change
- sys.dm_db_objects_impacted_on_version_change
ms.assetid: b94af834-c4f6-4a27-80a6-e8e71fa8793a
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 812f64934283d15674c8aa0ce1f305f7729f495f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmdbobjectsimpactedonversionchange-azure-sql-database"></a>sys.dm_db_objects_impacted_on_version_change (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Это системное представление уровня базы данных предназначено для отображения ранних предупреждений, позволяющих определить объекты, которые затрагиваются при обновлении выпуска в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Можно использовать это представление до или после обновления для получения полного перечисления затронутых объектов. Чтобы запросить полный отчет для всего сервера, потребуется запросить это представление в каждой базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|class|**int** NOT NULL|Класс объекта, который будет затронут:<br /><br /> **1** = ограничение<br /><br /> **7** = индексы и кучи|  
|class_desc|**nvarchar(60)** NOT NULL|Описание класса:<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **INDEX**|  
|major_id|**int** NOT NULL|Код объекта ограничения или код объекта таблицы, содержащей индекс или кучу.|  
|minor_id|**int** значение NULL|**Значение NULL** для ограничений<br /><br /> Index_id для индексов и куч|  
|dependency|**nvarchar(60)** NOT NULL|Описание зависимости, которая вызывает применение затрагиваемого ограничения или индекса. Такое же значение используется для предупреждений, созданных во время обновления.<br /><br /> Примеры:<br /><br /> **место** (для встроенных)<br /><br /> **Geometry** (для системы определяемого пользователем ТИПА)<br /><br /> **Geography::Parse** (для системы метод определяемого пользователем ТИПА)|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
## <a name="example"></a>Пример  
 В следующем примере показано запрос на **sys.dm_db_objects_impacted_on_version_change** для поиска объектов, затрагиваемых обновление до следующей версии  
  
```  
SELECT * FROM sys.dm_db_objects_disabled_on_version_change;  
GO  
```  
  
```  
class  class_desc        major_id    minor_id    dependency                       
------ ----------------- ----------- ----------- ----------   
1      OBJECT_OR_COLUMN  181575685   NULL        geometry                        
7      INDEX             37575172    1           geometry                        
7      INDEX             2121058592  1           geometry                        
1      OBJECT_OR_COLUMN  101575400   NULL        geometry     
```  
  
## <a name="remarks"></a>Замечания  
  
### <a name="how-to-update-impacted-objects"></a>Обновление затрагиваемых объектов  
 Далее описывается порядок действий по исправлению после обновления набора исправлений, которое будет доступно в июне.  
  
|Порядок|Затрагиваемый объект|Действие по исправлению|  
|-----------|---------------------|-----------------------|  
|1|**Индексы**|Перестроить индекс, определенный **sys.dm_db_objects_impacted_on_version_change** например:  `ALTER INDEX ALL ON <table> REBUILD`<br />либо<br />`ALTER TABLE <table> REBUILD`|  
|2|**Объект**|Все ограничения, определенные **sys.dm_db_objects_impacted_on_version_change** необходимо выполнить повторную после данных geometry и geography в базовой таблице. Для ограничений выполните проверку с помощью инструкции ALTER TABLE. <br />Например: <br />`ALTER TABLE <tab> WITH CHECK CHECK CONSTRAINT <constraint name>`<br />либо<br />`ALTER TABLE <tab> WITH CHECK CONSTRAINT ALL`|  
  
  
