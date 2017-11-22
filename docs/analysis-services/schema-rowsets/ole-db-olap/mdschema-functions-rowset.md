---
title: "Набор строк MDSCHEMA_FUNCTIONS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_FUNCTIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 446f89e34824cbb4ebde3d49bb3ceb686b4adafd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemafunctions-rowset"></a>Набор строк MDSCHEMA_FUNCTIONS
  Описывает функции, доступные клиентским приложениям, подключенным к базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_FUNCTIONS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
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
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
