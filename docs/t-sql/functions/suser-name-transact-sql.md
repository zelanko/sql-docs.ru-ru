---
title: SUSER_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 85d508acfb4ce6bb6a3d3ae9c65cc6a9d45c667b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43104254"
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
 Идентификационный номер учетной записи пользователя. Необязательный аргумент *server_user_id* имеет тип **int**. Аргумент *server_user_id* может быть идентификационным номером любого имени для входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также пользователя или группы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, которые обладают разрешениями на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если аргумент *server_user_id* не указан, возвращается идентификационное имя для входа текущего пользователя. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 идентификатор безопасности (SID) заменил идентификатор пользователя сервера (SUID).  
  
 SUSER_NAME возвращает имя для входа, которое присутствует в системной таблице **syslogins**.  
  
 SUSER_NAME можно использовать в списке выборки в предложении WHERE, а также везде, где разрешено использовать выражения. Вслед за функцией SUSER_NAME всегда должны следовать скобки, даже если параметр не указан.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует получение идентификационного имени учетной записи с идентификационным номером `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>См. также:  
 [SUSER_ID (Transact-SQL)](../../t-sql/functions/suser-id-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
