---
title: Набор строк DISCOVER_CONNECTIONS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_CONNECTIONS rowset
ms.assetid: e4703970-c31d-448c-ab68-503303c91aa4
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02c834a399f2dc6056831f2d4f84b65deb5ba503
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194304"
---
# <a name="discoverconnections-rowset"></a>Набор строк DISCOVER_CONNECTIONS
  Предоставляет сведения об использовании ресурсов и действиях, касающиеся соединений, открытых в настоящее время на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_CONNECTIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничения|Описание|  
|-----------------|--------------------|------------------|-----------------|  
|`CONNECTION_ID`|`DBTYPE_I4`|Да|Уникальное число, определяющее соединение.|  
|`CONNECTION_USER_NAME`|`DBTYPE_WSTR`|Да|Имя пользователя соединения.|  
|`CONNECTION_IMPERSONATED_USER_NAME`|`DBTYPE_WSTR`|Да|Зарезервировано для последующего использования. Службы Analysis Services всегда возвращают значение NULL для CONNECTION_IMPERSONATED_USER_NAME.|  
|`CONNECTION_HOST_NAME`|`DBTYPE_WSTR`|Да|Имя компьютера, на котором было инициировано соединение.|  
|`CONNECTION_HOST_APPLICATION`|`DBTYPE_WSTR`||Имя приложения, в котором было инициировано соединение.|  
|`CONNECTION_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время сервера в формате UTC на момент открытия соединения.|  
|`CONNECTION_ELAPSED_TIME_MS`|`DBTYPE_I8`|Да|Общее затраченное время (в миллисекундах) со времени начала работы соединения.|  
|`CONNECTION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время запуска на выполнение последней команды на сервере в формате UTC.|  
|`CONNECTION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время сервера в формате UTC на момент завершения выполнения последней команды.|  
|`CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS`|`DBTYPE_I8`|Да|Общее затраченное время (в миллисекундах) со времени выполнения последней команды.|  
|`CONNECTION_IDLE_TIME_MS`|`DBTYPE_I8`|Да|Время простоя (в миллисекундах) с момента открытия соединения.|  
|`CONNECTION_BYTES_SENT`|`DBTYPE_I8`||Накопленное число байтов, отправленных в соединении со времени начала работы соединения.|  
|`CONNECTION_DATA_BYTES_SENT`|`DBTYPE_I8`||Накопленное число байтов данных, отправленных в соединении со времени начала работы соединения.<br /><br /> Данные перемещаются в соединении в упакованном виде; это значение представляет количество отправленных данных в распакованном виде.|  
|`CONNECTION_BYTES_RECEIVED`|`DBTYPE_I8`||Накопленное число байтов, полученных в соединении со времени начала работы соединения.|  
|`CONNECTION_DATA_BYTES_RECEIVED`|`DBTYPE_I8`||Накопленное число байтов данных, полученных в соединении со времени начала работы соединения.<br /><br /> Данные перемещаются в соединении в упакованном виде; это значение представляет количество полученных данных в распакованном виде.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Соединения|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
