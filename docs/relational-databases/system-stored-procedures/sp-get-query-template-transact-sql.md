---
title: Хранимая процедура sp_get_query_template (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_query_template
- sp_get_query_template_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_query_template
ms.assetid: 85e9bef7-2417-41a8-befa-fe75507d9bf2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0d4d19f7b32297401ff036e61806308b54e44c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810282"
---
# <a name="spgetquerytemplate-transact-sql"></a>sp_get_query_template (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает запрос в параметризованной форме. Возвращаемые результаты имитируют параметризованную форму запроса, получаемую в результате принудительной параметризации. Хранимая процедура sp_get_query_template предназначена главным образом при создании структуры плана TEMPLATE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_get_query_template  
   [ @querytext = ] N'query_text'  
   , @templatetext OUTPUT   
   , @parameters OUTPUT   
```  
  
## <a name="arguments"></a>Аргументы  
 "*query_text*"  
 Запрос, для которого создается параметризованная версия. "*query_text*" должны быть заключены в одинарные кавычки и предваряться описателем Юникода n. N'*query_text*"— это значение, присваиваемое @querytext параметра. Тип **nvarchar(max)**.  
  
 @templatetext  
 Является выходным параметром типа **nvarchar(max)**, предназначенный для получения параметризованной формы *query_text* как строковый литерал.  
  
 @parameters  
 Является выходным параметром типа **nvarchar(max)**, предназначенный для получения параметров имена и типы данных, которые были параметризованы в строковый литерал @templatetext.  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_get_query_template возвращает ошибку, если:  
  
-   Невозможно параметризовать значения констант в *query_text*.  
  
-   *query_text* имеет значение NULL, не является строкой Юникода, синтаксически неверен или не удается скомпилировать.  
  
 Если хранимая процедура sp_get_query_template возвращает ошибку, он не изменяет значения @templatetext и @parameters выходных параметров.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в роли базы данных public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выдается параметризованная форма запроса, в котором содержатся два литеральных значения константы.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @my_templatetext nvarchar(max)  
DECLARE @my_parameters nvarchar(max)  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
        FROM Production.ProductModel pm   
        INNER JOIN Production.ProductInventory pi  
        ON pm.ProductModelID = pi.ProductID  
        WHERE pi.ProductID = 2  
        GROUP BY pi.ProductID, pi.Quantity  
        HAVING SUM(pi.Quantity) > 400',  
@my_templatetext OUTPUT,  
@my_parameters OUTPUT;  
SELECT @my_templatetext;  
SELECT @my_parameters;  
```  
  
 Ниже приведены параметризованные результаты в аргументе `@my_templatetext``OUTPUT`.  
  
 `select pi . ProductID , SUM ( pi . Quantity ) as Total`  
  
 `from Production . ProductModel pm`  
  
 `inner join Production . ProductInventory pi`  
  
 `on pm . ProductModelID = pi . ProductID`  
  
 `where pi . ProductID = @0`  
  
 `group by pi . ProductID , pi . Quantity`  
  
 `having SUM ( pi . Quantity ) > 400`  
  
 Обратите внимание, что первая константа `2`, преобразуется в параметр. Второй литерал, `400`, в параметр не преобразуется, так как он содержится внутри предложения `HAVING`. Результаты, возвращенные sp_get_query_template, имитируют параметризованную форму запроса, если параметр PARAMETERIZATION инструкции ALTER DATABASE установлен в FORCED.  
  
 Ниже приведены параметризованные результаты в аргументе `@my_parameters OUTPUT`.  
  
```  
@0 int  
```  
  
> [!NOTE]  
>  Порядок и имена параметров, возвращаемых из процедуры sp_get_query_template, могут измениться при наложении исправлений, пакетов обновлений и обновлениях версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обновление версии может также стать причиной получения отличающегося набора параметризуемых констант для того же запроса и изменения формата выдачи результатов для обоих выходных параметров.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Указание механизма параметризации запросов с помощью структур плана](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)  
  
  
