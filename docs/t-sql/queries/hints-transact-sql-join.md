---
title: "Указания (Transact-SQL) в соединении | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Join Hint
- Join_Hint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HASH join hint
- REMOTE join hint
- LOOP join hint
- join hints
- MERGE join hint
- hints [SQL Server], join
ms.assetid: 09069f4a-f2e3-4717-80e1-c0110058efc4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9e0652286a1f9da56df54ec2e00eee5bea20e1be
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="hints-transact-sql---join"></a>Указания (Transact-SQL) - соединения
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Подсказки в соединении указывают оптимизатору запросов на выбор определенной стратегии соединения двух таблиц в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Общие сведения о соединениях и синтаксисе соединения см. в разделе [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
> [!IMPORTANT]  
>  Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оптимизатор запросов обычно выбирает наилучший план выполнения для запроса, мы рекомендуем, подсказки, включая \<join_hint >, используется только в качестве последнего средства опытным разработчикам и администраторам баз данных.
  
 **Область применения:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<join_hint> ::=   
     { LOOP | HASH | MERGE | REMOTE }  
```  
  
## <a name="arguments"></a>Аргументы  
 LOOP | HASH | MERGE  
 Задает использование циклов, хэша и операций объединения при соединении в запросе. Использование LOOP | HASH | MERGE JOIN автоматически создает соединение между двумя таблицами. Аргумент LOOP не может указываться вместе с параметрами RIGHT или FULL в качестве типа соединения.  
  
 REMOTE  
 Задает, что операция соединения проводится на сайте в таблице, расположенной справа. Данный аргумент удобно использовать в случае, когда таблица, расположенная слева, является локальной, а справа располагается удаленная таблица. Аргумент REMOTE может использоваться в случае, когда в таблице слева содержится меньшее количество строк, чем в таблице справа.  
  
 Если таблица, расположенная справа, является локальной, то операция соединения также проводится локально. Если обе таблицы являются удаленными, но расположены в различных источниках данных, то при задании аргумента REMOTE операция соединения проводится на сайте в таблице, расположенной справа. Если обе таблицы являются удаленными таблицами в одном источнике данных, то аргумент REMOTE не требуется.  
  
 Аргумент REMOTE не может быть использован для сравнения в предикате соединения значений, одно из которых приведено к другим параметрам сортировки с помощью предложения COLLATE.  
  
 Аргумент REMOTE может быть использован только при операциях INNER JOIN.  
  
## <a name="remarks"></a>Remarks  
 Указания по соединению задаются в запросе в предложении FROM. Указания по соединению принудительно активируют стратегию соединения между двумя таблицами. При задании указаний соединений для любых двух таблиц оптимизатор запросов принудительно автоматически активирует порядок соединения для всех соединенных таблиц в запросе, основанном на положении ключевого слова ON. При использовании CROSS JOIN без предложения ON для определения порядка соединения могут использоваться скобки.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-hash"></a>A. Использование HASH  
 В следующем примере операция `JOIN` в запросе выполняется с помощью соединения `HASH`. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT p.Name, pr.ProductReviewID  
FROM Production.Product AS p  
LEFT OUTER HASH JOIN Production.ProductReview AS pr  
ON p.ProductID = pr.ProductID  
ORDER BY ProductReviewID DESC;  
```  
  
### <a name="b-using-loop"></a>Б. Использование LOOP  
 В следующем примере операция `JOIN` в запросе выполняется с помощью соединения `LOOP`. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
    INNER LOOP JOIN Sales.SalesPerson AS sp  
    ON spqh.SalesPersonID = sp.SalesPersonID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
### <a name="c-using-merge"></a>В. Использование инструкции MERGE  
 В следующем примере операция `JOIN` в запросе выполняется с помощью соединения `MERGE`. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT poh.PurchaseOrderID, poh.OrderDate, pod.ProductID, pod.DueDate, poh.VendorID   
FROM Purchasing.PurchaseOrderHeader AS poh  
INNER MERGE JOIN Purchasing.PurchaseOrderDetail AS pod   
    ON poh.PurchaseOrderID = pod.PurchaseOrderID;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Указания &#40; Transact-SQL &#41;](../../t-sql/queries/hints-transact-sql.md)  
  
  
