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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d7409d28b6a21a033c139c63ca6d6e7524e6ba50
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783765"
---
# <a name="sp_dsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @dsn = ] 'dsn'`Имя DSN ODBC или связанный сервер OLE DB. *DSN* имеет тип **varchar (128)** и не имеет значения по умолчанию.  
  
`[ @infotype = ] 'info_type'`Тип возвращаемых данных. Если *info_type* не указан или указано значение null, возвращаются все типы данных. *info_type* имеет тип **varchar (128)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Применение|Описание:|  
|-----------|-----------------|  
|**DBMS_NAME**|Указывает имя поставщика источника данных.|  
|**DBMS_VERSION**|Указывает версию источника данных.|  
|**DATABASE_NAME**|Указывает имя базы данных.|  
|**SQL_SUBSCRIBER**|Указывает, что источник данных может быть подписчиком.|  
  
`[ @login = ] 'login'`Имя входа для источника данных. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *имя для входа*— **varchar (128)** и значение по умолчанию NULL.  
  
`[ @password = ] 'password'`Пароль для имени входа. Если источник данных содержит имя входа, то следует установить значение NULL или опустить этот параметр. *Password*имеет тип **varchar (128)** и значение по умолчанию NULL.  
  
`[ @dso_type = ] dso_type`Тип источника данных. *dso_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Применение|Описание:|  
|-----------|-----------------|  
|**1** (по умолчанию)|Источник данных ODBC|  
|**3**|OLE DB, источник данных|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Тип сведений**|**nvarchar (64)**|Типы данных, например: DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER.|  
|**Значение**|**nvarchar(512)**|Значение связанного типа данных.|  
  
## <a name="remarks"></a>Примечания  
 **sp_dsninfo** используется во всех типах репликации.  
  
 **sp_dsninfo** извлекает сведения об источнике данных ODBC или OLE DB, которые показывают, может ли база данных использоваться для репликации или выполнения запросов.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_dsninfo**.  
  
## <a name="see-also"></a>См. также  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
