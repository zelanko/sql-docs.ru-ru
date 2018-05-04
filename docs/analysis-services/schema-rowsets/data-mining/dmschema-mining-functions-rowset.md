---
title: Набор строк DMSCHEMA_MINING_FUNCTIONS | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_FUNCTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70dd46fa691630b2ebdb9a86e980fbad6e41f6b0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
