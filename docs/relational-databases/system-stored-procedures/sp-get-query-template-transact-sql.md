---
title: sp_get_query_template (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 9841e7815f31af26aeeb3ed0f4783d3a36d83030
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124084"
---
# <a name="sp_get_query_template-transact-sql"></a>sp_get_query_template (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает запрос в параметризованной форме. Возвращаемые результаты имитируют параметризованную форму запроса, получаемую в результате принудительной параметризации. sp_get_query_template используется в основном при создании руководств планов шаблонов.  
  
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
 Запрос, для которого создается параметризованная версия. "*query_text*" необходимо заключать в одинарные кавычки и предшествовать спецификатору N Юникода. N '*query_text*' — это значение, присваиваемое @querytext параметру. Это относится к типу **nvarchar (max)**.  
  
 @templatetext  
 Является выходным параметром типа **nvarchar (max)**, предоставленным как указано, для получения параметризованной формы *query_text* в виде строкового литерала.  
  
 @parameters  
 Является выходным параметром типа **nvarchar (max)**, который указан как указанный, для получения строкового литерала имен параметров и типов данных, которые были параметризованы в @templatetext.  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_get_query_template возвращает ошибку, если:  
  
-   Он не выполняет параметризацию значений констант литерала в *query_text*.  
  
-   *query_text* имеет значение null, не является строкой Юникода, синтаксически недопустимым или не может быть скомпилировано.  
  
 Если sp_get_query_template возвращает ошибку, значения выходных параметров @templatetext и @parameters не изменяются.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Указание механизма параметризации запросов с помощью структур плана](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)  
  
  
