---
title: Набор строк DISCOVER_DB_CONNECTIONS | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f22c330fcc1deef1e86f4442ed8524235a3ba5c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295554"
---
# <a name="discoverdbconnections-rowset"></a>Набор строк DISCOVER_DB_CONNECTIONS
  Предоставляет сведения об использовании и действиях по открытым в настоящий момент соединениям сервера с базой данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_DB_CONNECTIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CONNECTION_CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных, с которой установлено текущее соединение.|  
|`CONNECTION_ID`|`DBTYPE_I4`||Уникальное число, определяющее соединение.|  
|`CONNECTION_IDLE_TIME_MS`|`DBTYPE_I8`||Время простоя (в миллисекундах) с момента открытия соединения.|  
|`CONNECTION_IN_USE`|`DBTYPE_I4`||Показывает активность соединения: 1 — активно, 0 — простаивает.|  
|`CONNECTION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время сервера в формате UTC на момент завершения выполнения последней команды.|  
|`CONNECTION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время на сервере в формате UTC, когда в последний раз запускалось выполнение команды.|  
|`CONNECTION_SERVER_NAME`|`DBTYPE_WSTR`||Имя сервера, с которым в настоящий момент установлено соединение.|  
|`CONNECTION_SPID`|`DBTYPE_I4`||Идентификатор сеанса.|  
|`CONNECTION_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время сервера в формате UTC на момент открытия соединения.|  
|`CONNECTION_USAGE_TIME_MS`|`DBTYPE_I8`||Время активной работы соединения (в миллисекундах) с момента начала соединения.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Сведения в наборе строк `DISCOVER_DB_CONNECTIONS` будут отображаться только тогда, когда служба установит соединение с реляционными источниками данных.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_DB_CONNECTIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Необязательный параметр.|  
|CONNECTION_IN_USE|DBTYPE_I4|Необязательный параметр.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Необязательный параметр.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Обязательный.|  
|CONNECTION_SPID|DBTYPE_I4|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
