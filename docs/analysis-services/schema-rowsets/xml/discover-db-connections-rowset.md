---
title: Набор строк DISCOVER_DB_CONNECTIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3680b130dabcb13d6b9a518e54389aa13be441eb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="discoverdbconnections-rowset"></a>Набор строк DISCOVER_DB_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения об использовании и действиях по открытым в настоящий момент соединениям сервера с базой данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_DB_CONNECTIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Имя базы данных, с которой установлено текущее соединение.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Уникальное число, определяющее соединение.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Время простоя (в миллисекундах) с момента открытия соединения.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||Показывает активность соединения: 1 — активно, 0 — простаивает.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент завершения выполнения последней команды.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время на сервере в формате UTC, когда в последний раз запускалось выполнение команды.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Имя сервера, с которым в настоящий момент установлено соединение.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||Идентификатор сеанса.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент открытия соединения.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Время активной работы соединения (в миллисекундах) с момента начала соединения.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Сведения в наборе строк **DISCOVER_DB_CONNECTIONS** будут отображаться только тогда, когда служба установит соединение с реляционными источниками данных.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_DB_CONNECTIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Необязательно.|  
|CONNECTION_IN_USE|DBTYPE_I4|Необязательно.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Необязательно.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Обязательный.|  
|CONNECTION_SPID|DBTYPE_I4|Необязательно.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
