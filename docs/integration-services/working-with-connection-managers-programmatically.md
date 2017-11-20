---
title: "Работа с диспетчерами соединений программным образом | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9093b9eadce231aea248cd04c2b57dc5dd5e1a76
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-connection-managers-programmatically"></a>Работа с диспетчерами соединений программным образом
  В [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], метод AcquireConnection связанного класса диспетчера соединений — метод, который вызывается наиболее часто при работе с диспетчерами соединений в управляемом коде. При написании управляемого кода, необходимо вызвать метод AcquireConnection для использования функции соединения диспетчера. Этот метод должен быть вызван вне зависимости от того, создается ли управляемый код для задачи «Скрипт», компонента скрипта, пользовательского объекта или пользовательского приложения.  
  
 Для успешного вызова метода AcquireConnection необходимо знать ответы на следующие вопросы:  
  
-   **Какие диспетчеры соединений возвращают управляемый объект из метода AcquireConnection?**  
  
     Многие диспетчеры соединений возвращают неуправляемые COM-объекты (System.__ComObject) и эти объекты сложно использовать из управляемого кода. Список таких диспетчеров соединений включает часто используемый диспетчер соединений OLE DB.  
  
-   **Для диспетчеров соединений, возвращающие управляемый объект какие объекты методы AcquireConnection возвращает?**  
  
     Чтобы привести возвращаемое значение к соответствующему типу, необходимо знать, какой тип объектов, возвращаемое методом AcquireConnection. Например, метод AcquireConnection для [!INCLUDE[vstecado](../includes/vstecado-md.md)] диспетчер соединений возвращает открытый объект SqlConnection при использовании поставщика SqlClient. Тем не менее метода AcquireConnection диспетчера соединений файлов возвращает просто строку.  
  
 Данных раздел содержит ответы на эти вопросы о диспетчерах соединений включенных в службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Диспетчеры соединений, не возвращающие управляемый объект  
 В следующей таблице перечислены диспетчеры соединений, которые возвращают собственный COM-объект (System.__ComObject) из метода AcquireConnection. Эти неуправляемые объекты сложно использовать в управляемом коде.  
  
|Тип диспетчера соединений|Имя диспетчера соединений|  
|-----------------------------|-----------------------------|  
|ADO|Диспетчер соединений ADO|  
|MSOLAP90|Диспетчер соединений служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|  
|EXCEL|Диспетчер соединений с Excel|  
|FTP|диспетчер FTP-соединений|  
|HTTP|диспетчер HTTP-соединений|  
|интерфейс ODBC|диспетчер соединений ODBC|  
|OLEDB|диспетчер соединений OLE DB|  
  
 Как правило, можно использовать [!INCLUDE[vstecado](../includes/vstecado-md.md)] диспетчера соединений из управляемого кода для подключения к источнику данных ADO, Excel, ODBC или OLE DB.  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Значения, возвращаемые методом AcquireConnection  
 В следующей таблице перечислены диспетчеры соединений, которые возвращают управляемый объект из метода AcquireConnection. Эти управляемые объекты легко использовать в управляемом коде.  
  
|Тип диспетчера соединений|Имя диспетчера соединений|Тип возвращаемого значения|Дополнительные сведения|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Диспетчер соединений служб [!INCLUDE[vstecado](../includes/vstecado-md.md)]|**System.Data.SqlClient.SqlConnection**||  
|FILE|диспетчер соединения файлов|**Строка System.String**|Путь к файлу.|  
|FLATFILE|Диспетчер соединений с неструктурированными файлами|**Строка System.String**|Путь к файлу.|  
|MSMQ|диспетчер соединений MSMQ|**System.Messaging.MessageQueue**||  
|MULTIFILE|диспетчер соединений с несколькими файлами|**Строка System.String**|Путь к одному из файлов.|  
|MULTIFLATFILE|диспетчер соединения с несколькими неструктурированными файлами|**Строка System.String**|Путь к одному из файлов.|  
|SMOServer|SMO, диспетчер соединений|**Microsoft.SqlServer.Management.Smo.Server**||  
|SMTP|Диспетчер соединений SMTP|**Строка System.String**|Например: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`.|  
|WMI|Диспетчер WMI-соединений|**System.Management.ManagementScope**||  
|SQLMOBILE|Диспетчер соединений SQL Server Compact|**System.Data.SqlServerCe.SqlCeConnection**||  
  
## <a name="see-also"></a>См. также:  
 [Подключение к источникам данных в задаче «скрипт»](../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Подключение к источникам данных в компоненте скрипта](../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Соединение с источниками данных в пользовательской задаче](../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  

