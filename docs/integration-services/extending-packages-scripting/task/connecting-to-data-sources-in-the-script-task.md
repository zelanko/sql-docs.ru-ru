---
description: Соединение с источниками данных в задаче «Скрипт»
title: Соединение с источниками данных в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d54dc51681e96ba34ec33f1a899f61983145c4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430236"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Соединение с источниками данных в задаче «Скрипт»

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Диспетчеры соединений обеспечивают доступ к источникам данных, которые были настроены в пакете. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 Задача "Скрипт" может обращаться к диспетчерам соединений через свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> объекта **Dts**. Каждый диспетчер соединений в коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections> хранит сведения о том, как соединиться с базовым источником данных.  
  
 При вызове метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> диспетчера соединений диспетчер соединяется с источником данных, если соединение еще не было установлено, и возвращает соответствующее соединение или сведения о соединении для использования в коде задачи «Скрипт».  
  
> [!NOTE]  
>  Прежде чем вызывать метод **AcquireConnection**, необходимо знать тип соединения, возвращаемого диспетчером соединений. Поскольку в задачу "Скрипт" включен параметр **Option Strict**, перед использованием необходимо привести подключение, возвращаемое с типом **Object**, к подходящему типу подключения.  
  
 Можно воспользоваться методом <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections>, возвращаемой свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>, чтобы выполнить поиск существующего соединения, прежде чем использовать соединение в коде.  
  
> [!IMPORTANT]  
>  В управляемом коде задачи "Скрипт" нельзя вызывать метод AcquireConnection диспетчеров соединений, возвращающих неуправляемые объекты, например диспетчера соединений OLE DB или диспетчера соединений Excel. Однако можно считать свойство ConnectionString этих диспетчеров соединений и подключиться к источнику данных непосредственно в коде с помощью строки подключения **OledbConnection** из пространства имен **System.Data.OleDb**.  
>   
>  Если необходимо вызвать метод AcquireConnection диспетчера соединений, возвращающего неуправляемый объект, используйте диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. При настройке диспетчера соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] для использования поставщика OLE DB, он соединяется с помощью поставщика данных [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] для OLE DB. В этом случае метод AcquireConnection возвращает **System.Data.OleDb.OleDbConnection** вместо неуправляемого объекта. Чтобы настроить диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] для работы с источником данных Excel, выберите поставщик OLE DB [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для Jet (Майкрософт), укажите книгу Excel, а затем введите `Excel 8.0` (для Excel 97 и более поздних версий) в качестве значения параметра **Расширенные свойства** на странице **Все** диалогового окна **Диспетчер соединений**.  
  
## <a name="connections-example"></a>Пример соединений  
 В следующем примере демонстрируется, как получить доступ к диспетчерам соединений из задачи «Скрипт». В образце предполагается, что был создан и настроен диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] с именем **Test ADO.NET Connection** и диспетчер соединений с неструктурированными файлами с именем **Test Flat File Connection**. Обратите внимание, что диспетчер соединений [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] возвращает объект **SqlConnection**, который можно использовать немедленно для соединения с источником данных. Диспетчер соединений с неструктурированными файлами, в то же время, возвращает лишь строку, содержащую путь и имя файла. Необходимо использовать методы из пространства имен **System.IO**, чтобы открыть неструктурированный файл и работать с ним.  
  
```vb  
    Public Sub Main()

        Dim myADONETConnection As SqlClient.SqlConnection =
            DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction),
                SqlClient.SqlConnection)
        MsgBox(myADONETConnection.ConnectionString,
            MsgBoxStyle.Information, "ADO.NET Connection")

        Dim myFlatFileConnection As String =
            DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction),
                String)
        MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")

        Dts.TaskResult = ScriptResults.Success

    End Sub
```  
  
```csharp  
        public void Main()
        {
            SqlConnection myADONETConnection = 
                Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)
                as SqlConnection;
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");

            string myFlatFileConnection = 
                Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) 
                as string;
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");

            Dts.TaskResult = (int)ScriptResults.Success;
        }
```  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](https://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  
