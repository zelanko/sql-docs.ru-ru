---
title: IDENT_CURRENT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_CURRENT
- IDENT_CURRENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- last identity value generated for table
- identity values [SQL Server], last generated
- identity columns, current value
- IDENT_CURRENT function
ms.assetid: 21517ced-39f5-4cd8-8d9c-0a0b8aff554a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: faee4465ed79d064085efc8962de054989ef3b84
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65946416"
---
# <a name="identcurrent-transact-sql"></a>IDENT_CURRENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возврат последнего значения идентификатора, созданного для указанной таблицы или представления. Последнее созданное значение идентификатора может относиться к любому сеансу и любой области.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IDENT_CURRENT( 'table_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name*  
 Имя таблицы, что значение идентификатора возвращается. Аргумент *table_name* имеет тип **varchar** и не имеет значения по умолчанию.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **numeric(38,0)**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как IDENT_CURRENT, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Remarks  
 Функция IDENT_CURRENT аналогична функциям идентификаторов [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SCOPE_IDENTITY и @@IDENTITY. Все три функции возвращают созданными последними значения идентификаторов. Однако эти функции различаются областью действия и сеансом, в соответствии с которыми определяется термин *last*.  
  
-   IDENT_CURRENT возвращает последнее значение идентифицирующего столбца, созданное для конкретной таблицы в любом сеансе и области поиска.  
  
-   @@IDENTITY возвращает последнее значение идентификатора, созданное для любой таблицы в текущем сеансе по всем областям.  
  
-   SCOPE_IDENTITY возвращает последнее значение идентификатора, созданное для любой таблицы в текущем сеансе по текущей области поиска.  
  
 Если значение IDENT_CURRENT равно NULL (потому что таблица никогда не содержала строк или была усечена), функция IDENT_CURRENT возвращает начальное значение.  
  
 Неудачно завершившиеся инструкции и транзакции могут изменить текущий идентификатор таблицы и создать пропуски в значениях столбца идентификаторов. Для значения идентификатора никогда не производится откат, несмотря на то, что транзакция, пытавшаяся вставить в таблицу значение, не была зафиксирована. Например, если инструкция INSERT привела к ошибке из-за нарушения ограничения IGNORE_DUP_KEY, текущее значение идентификатора для таблицы все равно увеличивается.  
  
 Будьте внимательны при использовании функции IDENT_CURRENT для прогнозирования следующего создаваемого значения идентификатора. Фактически создаваемое значение может отличаться от полученного с помощью функций IDENT_CURRENT и IDENT_INCR, потому что в других сеансах тоже могут выполняться операции вставки.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-last-identity-value-generated-for-a-specified-table"></a>A. Возврат последнего значения идентификатора, созданного для указанной таблицы  
 В следующем примере возвращается последнее значение идентификатора, созданное для таблицы `Person.Address` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENT_CURRENT ('Person.Address') AS Current_Identity;  
GO  
```  
  
### <a name="b-comparing-identity-values-returned-by-identcurrent-identity-and-scopeidentity"></a>Б. Сравнение значений идентификатора, возвращаемых функциями IDENT_CURRENT, @@IDENTITY и SCOPE_IDENTITY  
 В следующем примере показаны различные идентификаторы, возвращаемые функциями `IDENT_CURRENT`, `@@IDENTITY` и `SCOPE_IDENTITY`.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N't6', N'U') IS NOT NULL   
    DROP TABLE t6;  
GO  
IF OBJECT_ID(N't7', N'U') IS NOT NULL   
    DROP TABLE t7;  
GO  
CREATE TABLE t6(id int IDENTITY);  
CREATE TABLE t7(id int IDENTITY(100,1));  
GO  
CREATE TRIGGER t6ins ON t6 FOR INSERT   
AS  
BEGIN  
   INSERT t7 DEFAULT VALUES  
END;  
GO  
--End of trigger definition  
  
SELECT id FROM t6;  
--IDs empty.  
  
SELECT id FROM t7;  
--ID is empty.  
  
--Do the following in Session 1  
INSERT t6 DEFAULT VALUES;  
SELECT @@IDENTITY;  
/*Returns the value 100. This was inserted by the trigger.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns the value 1. This was inserted by the   
INSERT statement two statements before this query.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns value inserted into t7, that is in the trigger.*/  
  
SELECT IDENT_CURRENT('t6');  
/* Returns value inserted into t6. This was the INSERT statement four statements before this query.*/  
  
-- Do the following in Session 2.  
SELECT @@IDENTITY;  
/* Returns NULL because there has been no INSERT action   
up to this point in this session.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns NULL because there has been no INSERT action   
up to this point in this scope in this session.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns the last value inserted into t7.*/  
```  
  
## <a name="see-also"></a>См. также:  
 [@@IDENTITY (Transact-SQL)](../../t-sql/functions/identity-transact-sql.md)   
 [SCOPE_IDENTITY (Transact-SQL)](../../t-sql/functions/scope-identity-transact-sql.md)   
 [IDENT_INCR (Transact-SQL)](../../t-sql/functions/ident-incr-transact-sql.md)   
 [IDENT_SEED (Transact-SQL)](../../t-sql/functions/ident-seed-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
