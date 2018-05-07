---
title: Набор строк DMSCHEMA_MINING_FUNCTIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f92a3028f9397283f8d5820c54d823e40b8fdc3d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingfunctions-rowset"></a>Набор строк DMSCHEMA_MINING_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает функции интеллектуального анализа данных, которые поддерживаются алгоритмами интеллектуального анализа данных, доступными на сервере, на котором эксплуатируются службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_FUNCTIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**||Имя алгоритма.|  
|**ИМЯ ФУНКЦИИ**|**DBTYPE_WSTR**||Имя функции.|  
|**СИГНАТУРА_ФУНКЦИИ**|**DBTYPE_WSTR**||Подпись функции.|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||Значение**FALSE** , если функция возвращает скалярное содержимое (такое как длина символьного аргумента); значение **TRUE** , если функция возвращает таблицы (такие как таблица гистограммы).|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание функции.|  
|**HELP_FILE**|**DBTYPE_WSTR**||Имя файла, который содержит документацию к этой функции.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||Идентификатор контекста справки для этой функции.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_FUNCTIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**ИМЯ ФУНКЦИИ**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
