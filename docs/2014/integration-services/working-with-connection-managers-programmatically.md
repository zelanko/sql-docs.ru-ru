---
title: Работа с диспетчерами соединений программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fc119c1339283353da8ab632785bb30cd65c057a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240934"
---
# <a name="working-with-connection-managers-programmatically"></a>Работа с диспетчерами соединений программным образом
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
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Диспетчер соединений служб [!INCLUDE[vstecado](../includes/vstecado-md.md)]|`System.Data.SqlClient.SqlConnection`||  
|FILE|диспетчер соединения файлов|`System.String`|Путь к файлу.|  
|FLATFILE|Диспетчер соединений с неструктурированными файлами|`System.String`|Путь к файлу.|  
|MSMQ|диспетчер соединений MSMQ|`System.Messaging.MessageQueue`||  
|MULTIFILE|диспетчер соединений с несколькими файлами|`System.String`|Путь к одному из файлов.|  
|MULTIFLATFILE|диспетчер соединения с несколькими неструктурированными файлами|`System.String`|Путь к одному из файлов.|  
|SMOServer|SMO, диспетчер соединений|`Microsoft.SqlServer.Management.Smo.Server`||  
|SMTP|Диспетчер соединений SMTP|`System.String`|Например: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`.|  
|WMI|Диспетчер WMI-соединений|`System.Management.ManagementScope`||  
|SQLMOBILE|Диспетчер соединений SQL Server Compact|`System.Data.SqlServerCe.SqlCeConnection`||  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Соединение с источниками данных в задаче "Скрипт"](extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Соединение с источниками данных в компоненте скрипта](extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Соединение с источниками данных в пользовательской задаче](extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  
