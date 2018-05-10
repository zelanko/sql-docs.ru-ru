---
title: DATABASE_PRINCIPAL_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATABASE_PRINCIPAL_ID_TSQL
- DATABASE_PRINCIPAL_ID
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], principals
- principal ID numbers [SQL Server]
- DATABASE_PRINCIPAL_ID function
- IDs [SQL Server], principals
ms.assetid: 908c7dd8-c10b-4658-92f6-0224f9835dd9
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e0583570ce9a4d11b2e4aa6c019c8f4ccc753239
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="databaseprincipalid-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификационный номер участника в текущей базе данных. Дополнительные сведения о субъектах см. в статье [Субъекты (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
*principal_name*  
Выражение типа **sysname**, представляющее субъект.  
Если аргумент *principal_name* не задан, возвращается идентификатор текущего пользователя. Необходимо поставить скобки.
  
## <a name="return-types"></a>Типы возвращаемых данных
**int**  
Значение NULL, когда участник базы данных не существует
  
## <a name="remarks"></a>Remarks  
Функция DATABASE_PRINCIPAL_ID может использоваться в списке выборки, в предложении WHERE и в любом месте, где разрешено выражение. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>A. Извлечение идентификатора текущего пользователя  
Следующий пример возвращает идентификатор участника базы данных текущего пользователя.
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>Б. Извлечение идентификатора указанного участника базы данных  
Следующий пример возвращает идентификатор участника базы данных для роли базы данных `db_owner`.
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[Иерархия разрешений (компонент Database Engine)](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  
