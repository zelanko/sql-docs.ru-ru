---
title: sp_enumdsn (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords:
- sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 57d9289ce7bf0667f347acffabbfcd4dd2a478c2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spenumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список имен всех определенных источников данных ODBC и OLE DB для сервера, работающего под определенной учетной записью [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Имя источника данных**|**sysname**|Имя источника данных.|  
|**Description**|**varchar(255)**|Описание источника данных.|  
|**Тип**|**int**|Тип источника данных:<br /><br /> **1** = ODBC DSN<br /><br /> **3** = источник данных OLE DB|  
|**Имя поставщика**|**varchar(255)**|Имя поставщика OLE DB. Для ODBC DSN возвращается значение NULL.|  
  
## <a name="remarks"></a>Замечания  
 Каждый [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы есть пользовательский контекст. Пользовательский контекст — это набор записей реестра, в который входят определения источников данных ODBC для пользователя. Пользовательскому контексту соответствует имя пользователя, под которым работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Например, если сервер работает в пользовательском контексте системной учетной записи, то все возвращаемые имена источников данных будут именами источников данных, связанных с системной учетной записью. Если сервер работает под частной пользовательской учетной записью, то будут возвращены имена источников данных только для частной учетной записи этого пользователя.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_enumdsn**.  
  
## <a name="see-also"></a>См. также  
 [sp_dsninfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
