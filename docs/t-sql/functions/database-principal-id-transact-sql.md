---
title: DATABASE_PRINCIPAL_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 337e64e16e1d1c2ab1d0130fde056eb0ef22df30
ms.sourcegitcommit: 869d4de6c807a37873b66e5479d2c5ceff9efb85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559436"
---
# <a name="databaseprincipalid-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Эта функция возвращает идентификационный номер субъекта в текущей базе данных. Дополнительные сведения о субъектах см. в статье [Субъекты &#40;ядро СУБД&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
*principal_name*  
Выражение типа **sysname**, представляющее субъект. Если аргумент *principal_name* не задан, `DATABASE_PRINCIPAL_ID` возвращает идентификатор текущего пользователя. `DATABASE_PRINCIPAL_ID` необходимо заключить в скобки.
  
## <a name="return-types"></a>Типы возвращаемых данных
**int**  
Значение NULL, если субъект базы данных не существует.
  
## <a name="remarks"></a>Remarks  
Используйте `DATABASE_PRINCIPAL_ID` в списке выбора, предложении WHERE или любом другом месте, допускающем выражение. Дополнительные сведения см. в статье [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>A. Извлечение идентификатора текущего пользователя  
В приведенном ниже примере возвращается идентификатор субъекта базы данных текущего пользователя.
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>Б. Извлечение идентификатора указанного участника базы данных  
В приведенном ниже примере возвращается идентификатор субъекта базы данных для роли базы данных `db_owner`.
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[Иерархия разрешений (компонент Database Engine)](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  
