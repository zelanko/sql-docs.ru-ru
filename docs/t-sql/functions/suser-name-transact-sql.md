---
title: "SUSER_NAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8d4eae9424d5c5cb2dbb2e7851d4e660fa0ba72
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Возвращает идентификационное имя учетной записи пользователя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *server_user_id*  
 Идентификационный номер учетной записи пользователя. *server_user_id*, необязательный — **int**. *server_user_id* может быть идентификационным номером любого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или [!INCLUDE[msCoName](../../includes/msconame-md.md)] пользователя или группу, имеющую разрешение на подключение к экземпляру компонента Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *server_user_id* — не указан, возвращается идентификационное имя входа для текущего пользователя. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 идентификатор безопасности (SID) заменил идентификатор пользователя сервера (SUID).  
  
 SUSER_NAME возвращает имя входа, только для имени входа, которое присутствует в **syslogins** системной таблицы.  
  
 SUSER_NAME можно использовать в списке выборки в предложении WHERE, а также везде, где разрешено использовать выражения. Вслед за функцией SUSER_NAME всегда должны следовать скобки, даже если параметр не указан.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует получение идентификационного имени учетной записи с идентификационным номером `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>См. также:  
 [SUSER_ID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-id-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

