---
title: Пример настраиваемого рабочего процесса (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9d72e31b8e4040353c9c93bceb65ca3c2be98788
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469049"
---
# <a name="custom-workflow-example-master-data-services"></a>Пример настраиваемого рабочего процесса (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] при создании библиотеки пользовательского класса рабочего процесса создается класс, реализующий интерфейс [Microsoft. MasterDataServices. Воркфловтипикстендер. иворкфловтипикстендер](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) . Этот интерфейс включает один метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)), который вызывается службой интеграции рабочего процесса MDS SQL Server при запуске рабочего процесса. Метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) содержит два параметра: *воркфловтипе* содержит текст, введенный в текстовом поле **тип рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , а *элемент* DataItem содержит метаданные и данные элементов для элемента, который активировал бизнес-правило рабочего процесса.  
  
## <a name="custom-workflow-example"></a>Пример пользовательского рабочего процесса  
 В следующем примере кода показано, как реализовать метод [Microsoft. MasterDataServices. воркфловтипикстендер. иворкфловтипикстендер. стартворкфлов *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) для извлечения атрибутов Name, Code и ластчгусернаме из XML-данных для элемента, который активировал бизнес-правило рабочего процесса, а также как вызывать хранимую процедуру для их вставки в другую базу данных. Пример XML-данных элемента с описанием содержащихся в них тегов см. в разделе [Описание XML настраиваемого рабочего процесса (службы Master Data Services)](create-a-custom-workflow-xml-description.md).  
  
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
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
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
 [Создание настраиваемого рабочего процесса (службы Master Data Services)](create-a-custom-workflow-master-data-services.md)  
  
  
