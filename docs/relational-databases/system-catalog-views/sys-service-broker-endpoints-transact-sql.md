---
title: "sys.service_broker_endpoints (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.service_broker_endpoints_TSQL
- service_broker_endpoints
- service_broker_endpoints_TSQL
- sys.service_broker_endpoints
dev_langs: TSQL
helpviewer_keywords: sys.service_broker_endpoints catalog view
ms.assetid: 6979ec9b-0043-411e-aafb-0226fa26c5ba
caps.latest.revision: "51"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7f9fdc08d74c9ca3e8c469462451fdd7bc5e49b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysservicebrokerendpoints-transact-sql"></a>sys.service_broker_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление каталога содержит по одной строке на каждую конечную точку компонента Service Broker. Для каждой строки в данном представлении имеется соответствующая строка с тем же **endpoint_id** в **sys.tcp_endpoints** представление, содержащее метаданные конфигурации TCP. TCP — единственный разрешенный протокол для компонента Service Broker.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**\<унаследованные столбцы >**|**--**|Наследует столбцы из [sys.endpoints &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_message_forwarding_enabled**|**bit**|Осуществляет пересылку сообщений поддержки конечных точек. Изначально установлено значение **0** (отключено). Не допускает значения NULL.|  
|**MESSAGE_FORWARDING_SIZE**|**int**|Максимальное количество мегабайтов **tempdb** дискового пространства, разрешенный для хранения перенаправляемых сообщений. Изначально установлено значение **10**. Не допускает значения NULL.|  
|**connection_auth**|**tinyint**|Тип проверки подлинности соединения, требуемый при подключении к этой конечной точке, один из следующих.<br /><br /> **1** -NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -СОГЛАСОВАНИЯ<br /><br /> **4** -СЕРТИФИКАТА<br /><br /> **5** -NTLM, CERTIFICATE<br /><br /> **6** -KERBEROS, CERTIFICATE<br /><br /> **7** -NEGOTIATE, CERTIFICATE<br /><br /> **8** -CERTIFICATE, NTLM<br /><br /> **9** -CERTIFICATE, KERBEROS<br /><br /> **10** -CERTIFICATE, NEGOTIATE<br /><br /> Не допускает значения NULL.|  
|**connection_auth_desc**|**nvarchar(60)**|Описание типа проверки подлинности, необходимого для соединения с данной конечной точкой, одно из следующих:<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM, CERTIFICATE<br /><br /> KERBEROS, CERTIFICATE<br /><br /> NEGOTIATE, CERTIFICATE<br /><br /> CERTIFICATE, NTLM<br /><br /> CERTIFICATE, KERBEROS<br /><br /> CERTIFICATE, NEGOTIATE<br /><br /> Допускает значение NULL.|  
|**идентификатор_сертификата**|**int**|Идентификатор сертификата, используемого для проверки подлинности (если таковой имеется).<br /><br /> 0 = используется проверка подлинности Windows.|  
|**encryption_algorithm**|**tinyint**|Алгоритм шифрования. Ниже приведены возможные значения с их описания и соответствующие параметры DDL.<br /><br /> **0** : NONE. Соответствующий параметр DDL: отключено.<br /><br /> **1** : RC4. Соответствующий параметр DDL: {необходимые &#124; Требуется алгоритм RC4}.<br /><br /> **2** : AES. Соответствующий параметр DDL: требуется алгоритм AES.<br /><br /> **3** : NONE, RC4. Соответствующий параметр DDL: {поддерживаемые &#124; Поддерживается алгоритм RC4}.<br /><br /> **4** : NONE, AES. Соответствующий параметр DDL: поддерживается алгоритм AES.<br /><br /> **5** : RC4, AES. Соответствующий параметр DDL: требуется алгоритм RC4 AES.<br /><br /> **6** : AES, RC4. Соответствующий параметр DDL: требуется алгоритм RC4 AES.<br /><br /> **7** : NONE, RC4, AES. Соответствующий параметр DDL: поддерживается алгоритм RC4 AES.<br /><br /> **8** : NONE, AES, RC4. Соответствующий параметр DDL: поддерживается алгоритм RC4 AES.<br /><br /> Не допускает значения NULL.|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Описание алгоритма шифрования. Ниже перечислены возможные значения и их соответствующие параметры DDL.<br /><br /> NONE: отключено<br /><br /> RC4: {необходимые &#124; Требуется алгоритм RC4}<br /><br /> AES: Требуется алгоритм AES<br /><br /> NONE, RC4: {поддерживается &#124; Поддерживается алгоритм RC4}<br /><br /> NONE, AES: Поддерживается алгоритм AES<br /><br /> RC4, AES: Требуется алгоритм RC4 AES<br /><br /> AES, RC4: Требуется алгоритм AES RC4<br /><br /> NONE, RC4, AES: Поддерживается алгоритм RC4 AES<br /><br /> NONE, AES, RC4: Поддерживается алгоритм AES RC4<br /><br /> Допускает значение NULL.|  
  
## <a name="remarks"></a>Замечания  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER ENDPOINT (Transact-SQL)](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)  
  
  
