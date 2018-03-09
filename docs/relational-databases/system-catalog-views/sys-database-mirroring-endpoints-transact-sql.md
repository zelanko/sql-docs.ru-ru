---
title: "sys.database_mirroring_endpoints (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_endpoints_TSQL
- database_mirroring_endpoints
- sys.database_mirroring_endpoints
- database_mirroring_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HADR [SQL Server], endpoint
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_endpoints catalog view
ms.assetid: f2285199-97ad-473c-a52d-270044dd862b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b9bc0c2229fe72265957d39991f2b67a1b395f0b
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabasemirroringendpoints-transact-sql"></a>sys.database_mirroring_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой конечной точки зеркального отображения базы данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Конечная точка зеркального отображения базы данных поддерживает как сеансы между участниками зеркального отображения базы данных и следящие серверы и сеансы между первичной группы доступности Always On и ее вторичных реплик.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<унаследованные столбцы >**|—|Наследует столбцы из **sys.endpoints** (Дополнительные сведения см. в разделе [sys.endpoints &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)).|  
|**role**|**tinyint**|Роль в зеркальном отображении, одна из следующих:<br /><br /> **0** = нет<br /><br /> **1** = partner<br /><br /> **2** = следящего сервера<br /><br /> **3** = All<br /><br /> Примечание: Это значение уместно только для зеркального отображения базы данных.|  
|**role_desc**|**nvarchar(60)**|Описание роли в зеркальном отображении, одно из следующих.<br /><br /> **NONE**<br /><br /> **ПАРТНЕРА**<br /><br /> **WITNESS**<br /><br /> **ALL**<br /><br /> Примечание: Это значение уместно только для зеркального отображения базы данных.|  
|**is_encryption_enabled**|**бит**|**1** означает, что шифрование включено.<br /><br /> **0** означает, что шифрование отключено.|  
|**connection_auth**|**tinyint**|Тип проверки подлинности соединения, требуемый при подключении к этой конечной точке, один из следующих.<br /><br /> **1** - NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -СОГЛАСОВАНИЯ<br /><br /> **4** -СЕРТИФИКАТА<br /><br /> **5** -NTLM, CERTIFICATE<br /><br /> **6** -KERBEROS, CERTIFICATE<br /><br /> **7** -NEGOTIATE, CERTIFICATE<br /><br /> **8** -CERTIFICATE, NTLM<br /><br /> **9** -CERTIFICATE, KERBEROS<br /><br /> **10** -CERTIFICATE, NEGOTIATE|  
|**connection_auth_desc**|**Nvarchar (60)**|Описание типа проверки подлинности, необходимого для подключения к конечной точке. Это один из следующих типов.<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM, CERTIFICATE<br /><br /> KERBEROS, CERTIFICATE<br /><br /> NEGOTIATE, CERTIFICATE<br /><br /> CERTIFICATE, NTLM<br /><br /> CERTIFICATE, KERBEROS<br /><br /> CERTIFICATE, NEGOTIATE|  
|**certificate_id**|**int**|Идентификатор сертификата, используемого для проверки подлинности (если таковой имеется).<br /><br /> 0 = используется проверка подлинности Windows.|  
|**encryption_algorithm**|**tinyint**|Алгоритм шифрования. Это один из следующих алгоритмов.<br /><br /> **0** — NONE<br /><br /> **1** – RC4<br /><br /> **2** — AES<br /><br /> **3** — NONE, RC4<br /><br /> **4** — NONE, AES<br /><br /> **5** — RC4, AES<br /><br /> **6** — AES, RC4<br /><br /> **7** — NONE, RC4, AES<br /><br /> **8** — NONE, AES, RC4|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Описание алгоритма шифрования. Это один из следующих алгоритмов.<br /><br /> None<br /><br /> RC4<br /><br /> AES<br /><br /> NONE, RC4<br /><br /> NONE, AES<br /><br /> RC4, AES<br /><br /> AES, RC4<br /><br /> NONE, RC4, AES<br /><br /> NONE, AES, RC4|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)   
 [sys.availability_replicas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.database_mirroring &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [Зеркального Endpoint &#40; SQL Server &#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
