---
title: sp_dsninfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63e4783420f9298e2e820341993774b81bbab7e3
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017497"
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
 [  **@dsn =**] **"***dsn***"**  
 Имя связанного сервера ODBC DSN или OLE DB. *DSN* — **varchar(128)**, не имеет значения по умолчанию.  
  
 [  **@infotype =**] **"***Тип_информации***"**  
 Возвращаемый тип информации. Если *Тип_информации* не указан или если указано значение NULL, возвращаются все типы информации. *Тип_информации* — **varchar(128)**, значение по умолчанию NULL, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**: DBMS_NAME**|Указывает имя поставщика источника данных.|  
|**DBMS_VERSION**|Указывает версию источника данных.|  
|**DATABASE_NAME**|Указывает имя базы данных.|  
|**SQL_SUBSCRIBER**|Указывает, что источник данных может быть подписчиком.|  
  
 [  **@login =**] **"***входа***"**  
 Имя входа для источника данных. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *Имя входа*— **varchar(128)**, значение по умолчанию NULL.  
  
 [  **@password =**] **"***пароль***"**  
 Пароль для данного имени входа. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *пароль*— **varchar(128)**, значение по умолчанию NULL.  
  
 [  **@dso_type=**] *dso_type*  
 Тип источника данных. *dso_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Источник данных ODBC|  
|**3**|OLE DB, источник данных|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Тип сведений**|**Nvarchar(64)**|Типы данных, например: DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER.|  
|**Value**|**nvarchar(512)**|Значение связанного типа данных.|  
  
## <a name="remarks"></a>Примечания  
 **sp_dsninfo** используется во всех типах репликации.  
  
 **sp_dsninfo** извлекает ODBC или OLE DB для источника данных, показывающий, является ли база данных может использоваться для репликации или запросы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_dsninfo**.  
  
## <a name="see-also"></a>См. также  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
