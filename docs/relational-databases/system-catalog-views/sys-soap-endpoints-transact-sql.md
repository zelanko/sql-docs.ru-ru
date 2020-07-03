---
title: sys. soap_endpoints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- soap_endpoints_TSQL
- sys.soap_endpoints
- soap_endpoints
- sys.soap_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.soap_endpoints catalog view
ms.assetid: f50dcbfc-02ed-4a19-9c07-c78a5a1b3224
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46f42c185a1be2cbf8742a14cc7d897f19430ca1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901174"
---
# <a name="syssoap_endpoints-transact-sql"></a>sys.soap_endpoints (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Содержит по одной строке для каждой конечной точки на сервере, которая содержит полезные данные типа SOAP. Для каждой строки в этом представлении существует соответствующая строка с тем же **endpoint_id** в представлении каталога **sys. http_endpoints** , которое содержит метаданные конфигурации HTTP.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**< наследуемые столбцы>**||Список столбцов, наследуемых этим представлением, см. в разделе [sys. endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_sql_language_enabled**|**bit**|1 = BATCHES = ENABLED означает, что нерегламентированные пакеты SQL допустимы для конечной точки.|  
|**wsdl_generator_procedure**|**nvarchar (776)**|Трехкомпонентное имя хранимой процедуры, которая реализует этот метод.<br /><br /> Для имен методов требуется использовать трехкомпонентные имена. Имена из одного, двух или четырех компонентов недопустимы.|  
|**default_database**|**sysname**|Имя базы данных по умолчанию, заданное в параметре DATABASE.<br /><br /> NULL = указан параметр DEFAULT.|  
|**default_namespace**|**nvarchar (384)**|Пространство имен по умолчанию, указанное в параметре NAMESPACE =, или `https://tempuri.org` значение, если вместо него был указан аргумент Default.|  
|**default_result_schema**|**tinyint**|Значение по умолчанию для параметра SCHEMA:<br /><br /> 0 = нет<br /><br /> 1 = STANDARD|  
|**default_result_schema_desc**|**nvarchar(60)**|Описание значения по умолчанию параметра SCHEMA:<br /><br /> NONE<br /><br /> STANDARD|  
|**is_xml_charset_enforced**|**bit**|0 = указан параметр CHARACTER_SET = SQL.<br /><br /> 1 = указан параметр CHARACTER_SET = XML.|  
|**is_session_enabled**|**bit**|0 = указан параметр SESSION = DISABLE.<br /><br /> 1 = указан параметр SESSION = ENABLED.|  
|**session_timeout**|**int**|Значение, указанное параметром SESSION_TIMEOUT.|  
|**login_type**|**nvarchar(60)**|Тип проверки подлинности, допустимый для этой конечной точки:<br /><br /> WINDOWS<br /><br /> MIXED|  
|**header_limit**|**int**|Максимально допустимый размер заголовка SOAP.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога конечных точек &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
