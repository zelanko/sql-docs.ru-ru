---
title: sys.endpoint_webmethods (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.endpoint_webmethods_TSQL
- sys.endpoint_webmethods
- endpoint_webmethods_TSQL
- sys.http_soap_methods_TSQL
- endpoint_webmethods
- sys.http_soap_methods
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoint_webmethods catalog view
ms.assetid: 7dad0cf6-eafa-47cf-98cc-75ba8d3c7959
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be8d6d8eb8f7e46d0967fa9ab5a0dc2a5ec12140
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035954"
---
# <a name="sysendpointwebmethods-transact-sql"></a>sys.endpoint_webmethods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Содержит строку для каждого метода FOR EACH SOAP, определенного в конечной точке HTTP с поддержкой протокола SOAP. Сочетание столбцов endpoint_id и namespace является уникальным значением.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|endpoint_id|**int**|Идентификатор конечной точки, относительно которой определен веб-метод.|  
|пространство имен|**nvarchar(384)**|Пространство имен для веб-метода.|  
|method_alias|**Nvarchar(64)**|Псевдоним для веб-метода.<br /><br /> Примечание: [!INCLUDE[tsql](../../includes/tsql-md.md)] идентификаторы допускаются символы, неразрешенные в именах методов WSDL.<br /><br /> Псевдоним используется для установки сопоставления имени в описании WSDL для конечной точки с фактическим базовым исполняемым объектом [!INCLUDE[tsql](../../includes/tsql-md.md)], который вызывается при запуске веб-метода.|  
|object_name|**nvarchar(776)**|Имя объекта, к которому перенаправляется веб-метод, заданное в виде ИМЯ = параметр. Части имени разделяются точкой (.) и выделяются квадратными скобками, `[``]`.<br /><br /> Имя объекта должно быть трехкомпонентным именем, заданным параметром WSDL.|  
|result_schema|**tinyint**|Аргумент, определяющий, какое определение XSD, если таковое имеется, отправляется в ответе:<br /><br /> 0 = нет<br /><br /> 1 = Стандартное<br /><br /> 2 = По умолчанию|  
|result_schema_desc|**nvarchar(60)**|Описание аргумента, определяющего, какое определение XSD, если таковое имеется, отправляется в ответе:<br /><br /> None<br /><br /> STANDARD<br /><br /> DEFAULT|  
|result_format|**tinyint**|Аргумент, определяющий способ форматирования результатов в ответе:<br /><br /> 1 = ALL_RESULTS (Все результаты)<br /><br /> 2 = ROWSETS_ONLY (Только наборы строк)<br /><br /> 3 = НЕТ|  
|result_format_desc|**nvarchar(60)**|Описание параметра, определяющего способ форматирования результатов в ответе:<br /><br /> ALL_RESULTS (Все результаты)<br /><br /> ROWSETS_ONLY (Только наборы строк)<br /><br /> None|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога конечных точек (Transact-SQL)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
