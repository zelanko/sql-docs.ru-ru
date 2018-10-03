---
title: Пример настраиваемого рабочего процесса (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 47ea8ae372cc796aa99da7dbb0fbdd99d922becd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129096"
---
# <a name="custom-workflow-example-master-data-services"></a>Пример настраиваемого рабочего процесса (службы Master Data Services)
  В веб-приложении [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] при создании библиотеки классов пользовательского рабочего процесса создается класс, реализующий интерфейс <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Этот интерфейс содержит один метод <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, который вызывается службой SQL Server MDS Workflow Integration Service при запуске рабочего процесса. Метод <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> содержит два параметра: параметр *workflowType* содержит текст, введенный в текстовое поле **Тип рабочего процесса** в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], а параметр *dataElement* содержит метаданные и данные элемента, который инициировал бизнес-правило рабочего процесса.  
  
## <a name="custom-workflow-example"></a>Пример пользовательского рабочего процесса  
 Следующий пример кода демонстрирует, как с помощью метода <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> можно извлечь атрибуты Name, Code и LastChgUserName из XML-данных элемента, вызвавшего срабатывание бизнес-правила рабочего процесса, а также как вызвать хранимую процедуру для вставки этих данных в другую базу данных. Пример XML-данных элемента с описанием содержащихся в них тегов см. в разделе [Описание XML настраиваемого рабочего процесса (службы Master Data Services)](create-a-custom-workflow-xml-description.md).  
  
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
  
  
