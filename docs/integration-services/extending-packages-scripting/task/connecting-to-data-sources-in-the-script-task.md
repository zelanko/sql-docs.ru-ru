---
title: "Подключение к источникам данных в задаче «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 825ff059476614085a338dd9c568031885bed64b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Соединение с источниками данных в задаче «Скрипт»
  Диспетчеры соединений обеспечивают доступ к источникам данных, которые были настроены в пакете. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 Задача «скрипт» можно получить доступ к диспетчерам соединений через <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> свойство **Dts** объекта. Каждый диспетчер соединений в коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections> хранит сведения о том, как соединиться с базовым источником данных.  
  
 При вызове метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> диспетчера соединений диспетчер соединяется с источником данных, если соединение еще не было установлено, и возвращает соответствующее соединение или сведения о соединении для использования в коде задачи «Скрипт».  
  
> [!NOTE]  
>  Необходимо знать тип соединения, возвращаемого диспетчером соединений перед вызовом **AcquireConnection**. Поскольку в задаче «скрипт» **Option Strict** включен, необходимо привести соединение, которое возвращается в виде типа **объекта**, к подходящему типу соединения перед его использованием.  
  
 Можно воспользоваться методом <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections>, возвращаемой свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>, чтобы выполнить поиск существующего соединения, прежде чем использовать соединение в коде.  
  
> [!IMPORTANT]  
>  Невозможно вызвать метод AcquireConnection диспетчеров соединений, которые возвращают неуправляемые объекты, такие как диспетчер соединений OLE DB и диспетчер соединений Excel, в управляемом коде задачи «скрипт». Тем не менее, можно считать свойство ConnectionString этих диспетчеров соединений и подключиться к источнику данных непосредственно в коде с помощью строки подключения с **OledbConnection** из **System.Data.OleDb** пространства имен.  
>   
>  Если необходимо вызвать метод AcquireConnection соединения диспетчера, возвращающего неуправляемый объект, используйте [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] диспетчера соединений. При настройке диспетчера соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] для использования поставщика OLE DB, он соединяется с помощью поставщика данных [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] для OLE DB. В этом случае метод AcquireConnection возвращает **System.Data.OleDb.OleDbConnection** вместо неуправляемого объекта. Настройка [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] диспетчер соединений для использования с источником данных Excel, выберите [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщик OLE DB для Jet, укажите файл Excel и введите `Excel 8.0` (для Excel 97 и более поздних версий) в качестве значения **расширенные свойства** на **все** страница **диспетчера соединений** диалоговое окно.  
  
## <a name="connections-example"></a>Пример соединений  
 В следующем примере демонстрируется, как получить доступ к диспетчерам соединений из задачи «Скрипт». Пример предполагает, что создан и настроен [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] диспетчер соединений с именем **Test ADO.NET Connection** и диспетчер соединений с неструктурированными файлами с именем **Test Flat File Connection**. Обратите внимание, что [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] диспетчер соединений возвращает **SqlConnection** объект, который можно использовать немедленно для подключения к источнику данных. Диспетчер соединений с неструктурированными файлами, в то же время, возвращает лишь строку, содержащую путь и имя файла. Необходимо использовать методы из **System.IO** пространство имен для открытия и работы с неструктурированного файла.  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

