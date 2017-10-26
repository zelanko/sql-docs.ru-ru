---
title: "Использование выходных данных FOR JSON в SQL Server и клиентских приложениях (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, using in client apps
- FOR JSON, using in SQL Server
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 1fa05e61c8c057141eceee65c5c1da39c5d4200e
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="use-for-json-output-in-sql-server-and-in-client-apps-sql-server"></a>Использование выходных данных FOR JSON в SQL Server и клиентских приложениях (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

В следующих примерах показаны некоторые способы использования предложения **FOR JSON** или выходных данных JSON в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в клиентских приложениях.  
  
## <a name="use-for-json-output-in-sql-server-variables"></a>Использование выходных данных FOR JSON в переменных SQL Server  
Выходные данные предложения FOR JSON имеют тип NVARCHAR(MAX), поэтому их можно назначить любой переменной, как показано в следующем примере.  
  
```sql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## <a name="use-for-json-output-in-sql-server-user-defined-functions"></a>Использование выходных данных FOR JSON в определяемых пользователем функциях SQL Server  
 Вы можете создать определяемые пользователем функции, которые форматируют результирующие наборы как JSON и возвращают эти выходные данные JSON. В следующем примере создается определяемая пользователем функция, которая производит выборку некоторых строк детализации заказа на продажу и форматирует их как массив JSON.  
  
```sql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
 RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
   RETURN (SELECT UnitPrice, OrderQty  
           FROM Sales.SalesOrderDetail  
           WHERE SalesOrderID = @salesOrderId  
           FOR JSON AUTO)  
END
```  
  
 Можно использовать эту функцию в пакете или запросе, как показано в следующем примере.  
  
```sql  
DECLARE @x NVARCHAR(MAX) = dbo.GetSalesOrderDetails(43659)

PRINT dbo.GetSalesOrderDetails(43659)

SELECT TOP 10
  H.*, dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details
FROM Sales.SalesOrderHeader H
```  
  
## <a name="merge-parent-and-child-data-into-a-single-table"></a>Слияние родительских и дочерних данных в одну таблицу  
В следующем примере каждый набор дочерних строк форматируется как массив JSON. Массив JSON становится значением столбца сведений в родительской таблице.  
  
```sql  
SELECT TOP 10 SalesOrderId, OrderDate,  
      (SELECT TOP 3 UnitPrice, OrderQty  
         FROM Sales.SalesOrderDetail D  
         WHERE H.SalesOrderId = D.SalesOrderID  
         FOR JSON AUTO) AS Details  
INTO SalesOrder  
FROM Sales.SalesOrderHeader H  
```  
  
## <a name="update-the-data-in-json-columns"></a>Обновление данных в столбцах JSON  
 В следующем примере показано, что можно обновлять значения столбцов, содержащих текст JSON.  
  
```sql  
UPDATE SalesOrder  
SET Details =  
     (SELECT TOP 1 UnitPrice, OrderQty  
       FROM Sales.SalesOrderDetail D  
       WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
      FOR JSON AUTO 
```  
  
## <a name="use-for-json-output-in-a-c-client-app"></a>Использование выходных данных FOR JSON в клиентском приложении C#  
 В приведенном ниже примере показано, как получить выходные данные JSON запроса в объект StringBuilder в клиентском приложении C#. Предположим, что переменная `queryWithForJson` содержит текст инструкции SELECT с предложением FOR JSON.  
  
```csharp  
var queryWithForJson = "SELECT ... FOR JSON";
var conn = new SqlConnection("<connection string>");
var cmd = new SqlCommand(queryWithForJson, conn);
conn.Open();
var jsonResult = new StringBuilder();
var reader = cmd.ExecuteReader();
if (!reader.HasRows)
{
    jsonResult.Append("[]");
}
else
{
    while (reader.Read())
    {
        jsonResult.Append(reader.GetValue(0).ToString());
    }
}
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).
 
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

