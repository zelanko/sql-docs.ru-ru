---
title: Пример пользовательского рабочего процесса
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 404fab4ed966fd8b29bc4160e7a7d721dd6397e7
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923092"
---
# <a name="create-a-custom-workflow---example"></a>Создание настраиваемого рабочего процесса — пример

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] при создании библиотеки классов настраиваемого рабочего процесса создается класс, реализующий интерфейс Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender. Этот интерфейс включает один метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) , который вызывается службой интеграции рабочего процесса MDS SQL Server при запуске рабочего процесса. Метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) содержит два параметра: *воркфловтипе* содержит текст, введенный в текстовом поле **тип рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , а *элемент* DataItem содержит метаданные и данные элементов для элемента, который активировал бизнес-правило рабочего процесса.  
  
## <a name="custom-workflow-example"></a>Пример пользовательского рабочего процесса  
 В следующем примере кода показано, как реализовать метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) для извлечения атрибутов Name, Code и ластчгусернаме из XML-данных для элемента, который активировал бизнес-правило рабочего процесса, а также как вызывать хранимую процедуру для их вставки в другую базу данных. Пример XML-данных элемента с описанием содержащихся в них тегов см. в разделе [Описание XML настраиваемого рабочего процесса (службы Master Data Services)](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("./MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("./MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("./MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Создание настраиваемого рабочего процесса (службы Master Data Services)](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
