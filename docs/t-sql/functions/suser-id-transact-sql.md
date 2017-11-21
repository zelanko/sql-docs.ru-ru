---
title: "SUSER_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e098c614f4e70cabf718ee4413920e61eb634c1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="suserid-transact-sql"></a>Идентификатор SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает идентификационный номер имени входа пользователя.  
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], функция SUSER_ID возвращает значение, указанное как **principal_id** в **sys.server_principals** представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *входа* **"**  
 Имя входа пользователя. *Имя входа* — **nchar**. Если *входа* указывается как **char**, *входа* неявно преобразуется в **nchar**. *Имя входа* может быть любой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа Windows пользователя или группы, имеющей разрешение на подключение к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *входа* — не указан, возвращается идентификационный номер имени входа для текущего пользователя. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Функция SUSER_ID возвращает идентификационные номера только для тех имен входа, которые были явным образом описаны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот идентификатор используется в рамках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отслеживания прав собственности и разрешений. Данный идентификатор не является эквивалентом идентификационной записи системы безопасности (SID) для имени входа, возвращаемого функцией SUSER_SID. Если *входа* является именем входа SQL Server, SID сопоставляется идентификатору GUID. Если *входа* является именем входа Windows или группы Windows, SID сопоставляется идентификатору безопасности Windows.  
  
 Функция SUSER_SID возвращает SUID только для имени входа, которое присутствует в **syslogins** системной таблицы.  
  
 Системные функции могут быть использованы в списке выбора, в предложении WHERE, и везде, где разрешено использование выражения, и за ними всегда должны следовать скобки, даже если не заданы никакие параметры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификационный номер для имени входа `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [Функция SUSER_SID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

