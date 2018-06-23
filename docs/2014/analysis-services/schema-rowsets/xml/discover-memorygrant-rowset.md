---
title: Набор строк DISCOVER_MEMORYGRANT | Документы Microsoft
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
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3066a924b572324fcf70dbec7aa726b9ba05f846
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191078"
---
# <a name="discovermemorygrant-rowset"></a>Набор строк DISCOVER_MEMORYGRANT
  Возвращает список предоставленных квот внутренней памяти, занятых заданиями, которые сейчас выполняются на сервере. Чтобы узнать, работает ли задание на сервере, используйте `Select * from $System.Discover_Jobs`.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_MEMORYGRANT` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`MEMORY_ID`|**DBTYPE_I8**||Число, идентифицирующее предоставление квоты памяти. Уникально в контексте одного запроса DISCOVER_MEMORYGRANT.|  
|`SPID`|`DBTYPE_I4`|Обязательно|SPID, который вы можете получить, запустив `Select * from $System.Discover_Sessions`.|  
|`CreationTime`|`DBTYPE_I8 DBTYPE_DBTIMESTAMP`||Время выдачи квоты.|  
|`LastRequestTime`|**DBTYPE_DBTIMESTAMP**||Время последнего изменения запроса квоты.|  
|`MemoryUsed`|`DBTYPE_I4`||Объем памяти, используемой во взаимосвязи с квотой.|  
|`MemoryGranted`|`DBTYPE_I4`||Объем памяти, предоставленной для использования задания, которое получает квоту памяти.|  
|`Blocked`|`DBTYPE_BOOL`||Логическое значение, указывающее на состояние блокировки задания. Значение true указывает, что задание блокируется из-за ожидания, пока другое задание освободит достаточную квоту, чтобы удовлетворить запрос квоты этого задания. Значение false указывает, что задание получило свою квоту и может выполняться.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  