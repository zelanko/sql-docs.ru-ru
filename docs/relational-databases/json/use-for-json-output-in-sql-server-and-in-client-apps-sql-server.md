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
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5331ff00081a7b79756ef14e771ab4a22d3e35ac
ms.lasthandoff: 04/11/2017

---
# <a name="use-for-json-output-in-sql-server-and-in-client-apps-sql-server"></a>Использование выходных данных FOR JSON в SQL Server и клиентских приложениях (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В следующих примерах показаны некоторые способы использования предложения **FOR JSON** или его выходных данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в клиентских приложениях.  
  
## <a name="use-for-json-output-in-sql-server-variables"></a>Использование выходных данных FOR JSON в переменных SQL Server  
 Выходные данные предложения FOR JSON имеют тип NVARCHAR(MAX), поэтому их можно назначить любой переменной, как показано в следующем примере.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## <a name="use-for-json-output-in-sql-server-user-defined-functions"></a>Использование выходных данных FOR JSON в определяемых пользователем функциях SQL Server  
 Вы можете создать определяемые пользователем функции, которые форматируют результирующие наборы как JSON и возвращают эти выходные данные JSON. В следующем примере создается определяемая пользователем функция, которая производит выборку некоторых строк детализации заказа на продажу и форматирует их как массив JSON.  
  
```tsql  
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
  
```tsql  
DECLARE @x NVARCHAR(MAX)=dbo.GetSalesOrderDetails(43659)

PRINT dbo.GetSalesOrderDetails(43659)

SELECT TOP 10
  H.*,dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details
FROM Sales.SalesOrderHeader H
```  
  
## <a name="merge-parent-and-child-data-into-a-single-table"></a>Слияние родительских и дочерних данных в одну таблицу  
 В следующем примере каждый набор дочерних строк форматируется как массив JSON и становится значением столбца сведений в родительской таблице.  
  
```tsql  
SELECT TOP 10 SalesOrderId, OrderDate,  
      (SELECT TOP 3 UnitPrice, OrderQty  
         FROM Sales.SalesOrderDetail D  
         WHERE H.SalesOrderId = D.SalesOrderID  
         FOR JSON AUTO) as Details  
INTO SalesOrder  
FROM Sales.SalesOrderHeader H  
```  
  
## <a name="update-the-data-in-json-columns"></a>Обновление данных в столбцах JSON  
 В следующем примере показано, что можно обновлять значения столбцов, содержащих текст JSON.  
  
```tsql  
UPDATE SalesOrder  
SET Details =  
     (SELECT TOP 1 UnitPrice, OrderQty  
       FROM Sales.SalesOrderDetail D  
       WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
      FOR JSON AUTO 
```  
  
## <a name="use-for-json-output-in-a-c-client-app"></a>Использование выходных данных FOR JSON в клиентском приложении C#  
 В приведенном ниже примере показано, как получить выходные данные JSON запроса в объект StringBuilder в клиентском приложении C#. Предположим, что переменная queryWithForJson содержит текст инструкции SELECT с предложением FOR JSON.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

