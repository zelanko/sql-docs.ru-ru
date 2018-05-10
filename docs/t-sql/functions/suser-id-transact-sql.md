---
title: SUSER_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 46cf5fde2cd11600a461b1f31e5fa48c73abe701
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="suserid-transact-sql"></a>Идентификатор SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Возвращает идентификационный номер имени входа пользователя.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], функция SUSER_ID возвращает значения, перечисленные в списке **principal_id** в представлении каталога **sys.server_principals**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *login* **'**  
 Имя входа пользователя. Аргумент *login* имеет тип **nchar**. Если в качестве *login* указано значение типа **char**, *login* неявно преобразуется в тип **nchar**. *login* может быть любым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пользователем или группой Windows с разрешением на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если аргумент *login* не задан, то возвращается идентификационный номер имени входа для текущего пользователя. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Функция SUSER_ID возвращает идентификационные номера только для тех имен входа, которые были явным образом описаны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот идентификатор используется в рамках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отслеживания прав собственности и разрешений. Данный идентификатор не является эквивалентом идентификационной записи системы безопасности (SID) для имени входа, возвращаемого функцией SUSER_SID. Если аргумент *login* является именем входа SQL Server, то значение SID сопоставляется с идентификатором GUID. Если аргумент *login* является именем входа Windows или группы Windows, то значение SID сопоставляется с идентификатором безопасности Windows.  
  
 Функция SUSER_SID возвращает SUID только для тех имен входа, для которых существуют записи в системной таблице **syslogins**.  
  
 Системные функции могут быть использованы в списке выбора, в предложении WHERE, и везде, где разрешено использование выражения, и за ними всегда должны следовать скобки, даже если не заданы никакие параметры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификационный номер для имени входа `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID (Transact-SQL)](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
