---
title: CUME_DIST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CUME_DIST
- CUME_DIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CUME_DIST function
- analytic functions, CUME_DIST
ms.assetid: 491b07f3-9ffd-4cdd-93e5-5abb636fc5ef
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1acd4feb0c65ee61b191a62fc0849f2156d46941
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824112"
---
# <a name="cumedist-transact-sql"></a>CUME_DIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эта функция вычисляет интегральное распределение значений в группе значений. Другими словами, `CUME_DIST` вычисляет относительное положение указанного значения в группе значений. Исходя из восходящего порядка сортировки, `CUME_DIST` значения для строки *r* — это число строк со значениями, меньшими или равными значению *r*, деленное на число строк, полученных в секции или результирующем наборе запроса. Функция `CUME_DIST` подобна функции `PERCENT_RANK`.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CUME_DIST( )  
    OVER ( [ partition_by_clause ] order_by_clause )  
  
```  
  
## <a name="arguments"></a>Аргументы  
OVER **(**[ *partition_by_clause* ] *order_by_clause*)  

*partition_by_clause* делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если аргумент *partition_by_clause* не указан, функция `CUME_DIST` обрабатывает все строки результирующего набора запроса как одну группу. Аргумент *order_by_clause* определяет логический порядок, в котором выполняется операция. Для функции `CUME_DIST` аргумент *order_by_clause* является обязательным. `CUME_DIST` не будет принимать \<строки или предложение диапазона> синтаксиса OVER. Дополнительные сведения см. в статье [SELECT — предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Типы возвращаемых данных
**float(53)**
  
## <a name="remarks"></a>Remarks  
`CUME_DIST` возвращает диапазон значений, которые больше 0 и меньше или равны 1. Для равных значений всегда вычисляется одно и то же значение накопительного распределения. `CUME_DIST` включает значения NULL по умолчанию и рассматривает их как наименьшие из возможных значений.
  
Функция `CUME_DIST` не детерминирована. Дополнительные сведения см. в статье [Детерминированные и недетерминированные функции](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Примеры  
В этом примере с помощью функции `CUME_DIST` выполняется вычисление процентиля заработной платы для каждого сотрудника указанного отдела. Значение, возвращаемое функцией `CUME_DIST`, представляет процент сотрудников, заработная плата которых меньше или равна заработной плате текущего сотрудника этого отдела. Функция `PERCENT_RANK` вычисляет процент заработной платы сотрудника в рамках отдела. Для секционирования строк результирующего набора по отделам в примере указывается значение *partition_by_clause*. Предложение ORDER BY в предложении OVER логически упорядочивает строки в каждой секции. Предложение ORDER BY в инструкции SELECT определяет порядок отображения результирующего набора.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT Department, LastName, Rate,   
       CUME_DIST () OVER (PARTITION BY Department ORDER BY Rate) AS CumeDist,   
       PERCENT_RANK() OVER (PARTITION BY Department ORDER BY Rate ) AS PctRank  
FROM HumanResources.vEmployeeDepartmentHistory AS edh  
    INNER JOIN HumanResources.EmployeePayHistory AS e    
    ON e.BusinessEntityID = edh.BusinessEntityID  
WHERE Department IN (N'Information Services',N'Document Control')   
ORDER BY Department, Rate DESC;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Department             LastName               Rate                  CumeDist               PctRank  
---------------------- ---------------------- --------------------- ---------------------- ----------------------  
Document Control       Arifin                 17.7885               1                      1  
Document Control       Norred                 16.8269               0.8                    0.5  
Document Control       Kharatishvili          16.8269               0.8                    0.5  
Document Control       Chai                   10.25                 0.4                    0  
Document Control       Berge                  10.25                 0.4                    0  
Information Services   Trenary                50.4808               1                      1  
Information Services   Conroy                 39.6635               0.9                    0.888888888888889  
Information Services   Ajenstat               38.4615               0.8                    0.666666666666667  
Information Services   Wilson                 38.4615               0.8                    0.666666666666667  
Information Services   Sharma                 32.4519               0.6                    0.444444444444444  
Information Services   Connelly               32.4519               0.6                    0.444444444444444  
Information Services   Berg                   27.4038               0.4                    0  
Information Services   Meyyappan              27.4038               0.4                    0  
Information Services   Bacon                  27.4038               0.4                    0  
Information Services   Bueno                  27.4038               0.4                    0  
(15 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[PERCENT_RANK (Transact-SQL)](../../t-sql/functions/percent-rank-transact-sql.md)
  
  
