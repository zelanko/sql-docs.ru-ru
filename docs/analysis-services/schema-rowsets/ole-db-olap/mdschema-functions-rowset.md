---
title: Набор строк MDSCHEMA_FUNCTIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 81c5ff06837dd9004be1ffc72be017a4991e902f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemafunctions-rowset"></a>Набор строк MDSCHEMA_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает функции, доступные клиентским приложениям, подключенным к базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_FUNCTIONS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|**ИМЯ ФУНКЦИИ**|**DBTYPE_WSTR**|Имя функции.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Описание функции.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**|Разделенный запятыми список параметров в формате языка [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic. Например, параметром может быть имя в виде строки.|  
|**ТИП**|**DBTYPE_I4**|**VARTYPE** типа возвращаемых данных функции.|  
|**ИСТОЧНИК**|**DBTYPE_I4**|Источник функции.<br /><br /> 1 для функций MDX.<br /><br /> 2 для определяемых пользователем функций.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Имя интерфейса для определяемых пользователем функций<br /><br /> Имя группы функций многомерных выражений.|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Имя библиотеки типов для определяемых пользователем функций. **Значение NULL** для функций многомерных Выражений.|  
|**DLL_NAME**|**DBTYPE_WSTR**|Имя сборки, реализующей определяемую пользователем функцию (необязательно).<br /><br /> Возвращает **VT_NULL** для функций многомерных Выражений.|  
|**HELP_FILE**|**DBTYPE_WSTR**|(Необязательно) Имя файла, который содержит справочную документацию для определяемой пользователем функции.<br /><br /> Возвращает **VT_NULL** для функций многомерных Выражений.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|(Необязательно) Возвращает идентификатор контекста справки для этой функции.|  
|**ОБЪЕКТ**|**DBTYPE_WSTR**|(Необязательно) Универсальное имя класса объектов, к которому применяется свойство. Например набор строк, соответствующий < level_name >. Функции элементов «**уровень**».<br /><br /> Возвращает **VT_NULL** для определяемых пользователем функций или функций MDX не свойства.|  
|**ЗАГОЛОВОК**|**DBTYPE_WSTR**|Отображаемый заголовок для функции.|  
  
 Набор строк отсортирован по **источника**, **INTERFACE_NAME**, **имя_функции**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_FUNCTIONS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**ИМЯ ФУНКЦИИ**|**DBTYPE_WSTR**|Необязательно.|  
|**ИСТОЧНИК**|**DBTYPE_I4**|Необязательно.|  
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
