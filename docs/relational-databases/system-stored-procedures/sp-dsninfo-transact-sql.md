---
title: sp_dsninfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6eacb453fc2f66f4b87790770fa50916916a27c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724029"
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об источнике данных ODBC или OLE DB, полученные от распространителя, связанного с текущим сервером. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dsn = ] 'dsn'` — Имя связанного сервера ODBC DSN или OLE DB. *DSN* — **varchar(128)** , не имеет значения по умолчанию.  
  
`[ @infotype = ] 'info_type'` — Тип возвращаемых сведений. Если *Тип_информации* не указан или если указано значение NULL, возвращаются все типы информации. *Тип_информации* — **varchar(128)** , значение по умолчанию NULL, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**DBMS_NAME**|Указывает имя поставщика источника данных.|  
|**DBMS_VERSION**|Указывает версию источника данных.|  
|**DATABASE_NAME**|Указывает имя базы данных.|  
|**SQL_SUBSCRIBER**|Указывает, что источник данных может быть подписчиком.|  
  
`[ @login = ] 'login'` — Это имя для источника данных. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *Имя входа*— **varchar(128)** , значение по умолчанию NULL.  
  
`[ @password = ] 'password'` — Пароль для имени входа. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *пароль*— **varchar(128)** , значение по умолчанию NULL.  
  
`[ @dso_type = ] dso_type` Является типом источника данных. *dso_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Источник данных ODBC|  
|**3**|OLE DB, источник данных|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Тип сведений**|**nvarchar(64)**|Типы данных, например: DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER.|  
|**Значение**|**nvarchar(512)**|Значение связанного типа данных.|  
  
## <a name="remarks"></a>Примечания  
 **sp_dsninfo** используется во всех типах репликации.  
  
 **sp_dsninfo** извлекает ODBC или OLE DB для источника данных, показывающий, является ли база данных может использоваться для репликации или запросы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_dsninfo**.  
  
## <a name="see-also"></a>См. также  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
