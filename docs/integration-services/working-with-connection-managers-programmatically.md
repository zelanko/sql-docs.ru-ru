---
title: Работа с диспетчерами соединений программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 14bce18a08fae02e7a0f8c2eed763d18b95c1a60
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65713633"
---
# <a name="working-with-connection-managers-programmatically"></a>Работа с диспетчерами соединений программным образом

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] метод AcquireConnection связанного класса диспетчера соединений вызывается наиболее часто при работе с диспетчерами соединений в управляемом коде. При создании управляемого кода необходимо вызвать метод AcquireConnection, чтобы воспользоваться функциональностью диспетчера соединений. Этот метод должен быть вызван вне зависимости от того, создается ли управляемый код для задачи «Скрипт», компонента скрипта, пользовательского объекта или пользовательского приложения.  
  
 Для успешного вызова метода AcquireConnection необходимо знать ответы на следующие вопросы:  
  
-   **Какие диспетчеры соединений возвращают управляемый объект из метода AcquireConnection?**  
  
     Многие диспетчеры соединений возвращают неуправляемые COM-объекты (System.__ComObject), которые сложно использовать в управляемом коде. Список таких диспетчеров соединений включает часто используемый диспетчер соединений OLE DB.  
  
-   **Какие объекты возвращают методы AcquireConnection для диспетчеров соединений, возвращающих управляемый объект?**  
  
     Чтобы привести возвращаемое значение к соответствующему типу, необходимо знать, объект какого типа возвращает метод AcquireConnection. Например, метод AcquireConnection диспетчера соединений [!INCLUDE[vstecado](../includes/vstecado-md.md)] возвращает открытый объект SqlConnection, если используется поставщик SqlClient. Однако метод AcquireConnection диспетчера соединения файлов возвращает просто строку.  
  
 Данных раздел содержит ответы на эти вопросы о диспетчерах соединений включенных в службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Диспетчеры соединений, не возвращающие управляемый объект  
 В следующей таблице перечислены диспетчеры соединений, возвращающие COM-объект в собственном режиме (System.__ComObject) из метода AcquireConnection. Эти неуправляемые объекты сложно использовать в управляемом коде.  
  
|Тип диспетчера соединений|Имя диспетчера соединений|  
|-----------------------------|-----------------------------|  
|ADO|Диспетчер соединений ADO|  
|MSOLAP90|Диспетчер соединений служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|  
|EXCEL|Диспетчер соединений с Excel|  
|FTP|диспетчер FTP-соединений|  
|HTTP|диспетчер HTTP-соединений|  
|интерфейс ODBC|диспетчер соединений ODBC|  
|OLEDB|диспетчер соединений OLE DB|  
  
 Как правило, для соединения с источником данных ADO, Excel, ODBC и OLE DB в управляемом коде можно использовать диспетчер соединений [!INCLUDE[vstecado](../includes/vstecado-md.md)].  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Значения, возвращаемые методом AcquireConnection  
 В следующей таблице перечислены диспетчеры соединений, возвращающие управляемый объект из метода AcquireConnection. Эти управляемые объекты легко использовать в управляемом коде.  
  
|Тип диспетчера соединений|Имя диспетчера соединений|Тип возвращаемого значения|Дополнительные сведения|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Диспетчер соединений служб [!INCLUDE[vstecado](../includes/vstecado-md.md)]|**System.Data.SqlClient.SqlConnection**||  
|FILE|диспетчер соединения файлов|**System.String**|Путь к файлу.|  
|FLATFILE|Диспетчер соединений с неструктурированными файлами|**System.String**|Путь к файлу.|  
|MSMQ|диспетчер соединений MSMQ|**System.Messaging.MessageQueue**||  
|MULTIFILE|диспетчер соединений с несколькими файлами|**System.String**|Путь к одному из файлов.|  
|MULTIFLATFILE|диспетчер соединения с несколькими неструктурированными файлами|**System.String**|Путь к одному из файлов.|  
|SMOServer|SMO, диспетчер соединений|**Microsoft.SqlServer.Management.Smo.Server**||  
|SMTP|Диспетчер соединений SMTP|**System.String**|Например: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI|Диспетчер WMI-соединений|**System.Management.ManagementScope**||  
|SQLMOBILE|Диспетчер соединений SQL Server Compact|**System.Data.SqlServerCe.SqlCeConnection**||  
  
## <a name="see-also"></a>См. также:  
 [Соединение с источниками данных в задаче "Скрипт"](../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Соединение с источниками данных в компоненте скрипта](../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Соединение с источниками данных в пользовательской задаче](../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  
