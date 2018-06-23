---
title: Набор строк DMSCHEMA_MINING_FUNCTIONS | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b5a60e18a57c15976e7a7bd5d5e31729e255869a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192323"
---
# <a name="dmschemaminingfunctions-rowset"></a>Набор строк DMSCHEMA_MINING_FUNCTIONS
  Описывает функции интеллектуального анализа данных, поддерживаемых алгоритмов интеллектуального анализа данных, доступных на сервере, на котором выполняется [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_FUNCTIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Имя алгоритма.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`||Имя функции.|  
|`FUNCTION_SIGNATURE`|`DBTYPE_WSTR`||Подпись функции.|  
|`RETURNS_TABLE`|`DBTYPE_BOOL`||Значение `FALSE`, если функция возвращает скалярное содержимое (такое как длина символьного аргумента); значение `TRUE`, если функция возвращает таблицы (такие как таблица гистограммы).|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание функции.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Имя файла, который содержит документацию к этой функции.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||Идентификатор контекста справки для этой функции.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_FUNCTIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  