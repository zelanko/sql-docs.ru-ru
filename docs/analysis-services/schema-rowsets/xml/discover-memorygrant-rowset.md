---
title: "Набор строк DISCOVER_MEMORYGRANT | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9bf3896348044d084144fd2276ff31f617b202c3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discovermemorygrant-rowset"></a>Набор строк DISCOVER_MEMORYGRANT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает список внутренней памяти предоставленных квот, выполняемых заданий, запущенных на сервере. Чтобы узнать, работает ли задание на сервере, используйте `Select * from $System.Discover_Jobs`.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_MEMORYGRANT** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MEMORY_ID**|**DBTYPE_I8**||Число, идентифицирующее предоставление квоты памяти. Уникально в контексте одного запроса DISCOVER_MEMORYGRANT.|  
|**SPID**|**DBTYPE_I4**|Обязательно|SPID, который вы можете получить, запустив `Select * from $System.Discover_Sessions`.|  
|**CreationTime**|**DBTYPE_I8 DBTYPE_DBTIMESTAMP**||Время выдачи квоты.|  
|**LastRequestTime**|**DBTYPE_DBTIMESTAMP**||Время последнего изменения запроса квоты.|  
|**MemoryUsed**|**DBTYPE_I4**||Объем памяти, используемой во взаимосвязи с квотой.|  
|**MemoryGranted**|**DBTYPE_I4**||Объем памяти, предоставленной для использования задания, которое получает квоту памяти.|  
|**Заблокировано**|**DBTYPE_BOOL**||Логическое значение, указывающее на состояние блокировки задания. Значение true указывает, что задание блокируется из-за ожидания, пока другое задание освободит достаточную квоту, чтобы удовлетворить запрос квоты этого задания. Значение false указывает, что задание получило свою квоту и может выполняться.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
