---
title: Соединение с источниками данных в пользовательской задаче | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ccbf5658019279fc36be3afaa759856ca8441ebc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968674"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a>Соединение с источниками данных в пользовательской задаче
  Чтобы получить или сохранить данные, задачи соединяются с внешними источниками данных с помощью диспетчера соединений. Во время разработки диспетчер соединений представляет логическое соединение и описывает основные сведения, например имя сервера и любые свойства проверки подлинности. Во время выполнения задачи вызывают метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> диспетчера соединений, чтобы установить физическое соединение с источником данных.  
  
 Поскольку пакет может содержать множество задач, каждая из которых может иметь соединения с различными источниками данных, пакет отслеживает все диспетчеры соединений в коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Connections>. Задачи используют коллекцию в своем пакете для поиска диспетчера соединений, который они смогут использовать во время проверки и выполнения. Коллекция <xref:Microsoft.SqlServer.Dts.Runtime.Connections> является первым параметром для методов <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
 Можно предотвратить использование задачи неподходящего диспетчера соединений, отобразив для пользователя объекты <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> из коллекции с помощью диалогового окна или раскрывающегося списка в графическом пользовательском интерфейсе. При этом пользователь получит возможность выбирать только из числа тех объектов <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, которые относятся к подходящему типу и содержатся в пакете.  
  
 Задачи вызывают метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A>, чтобы установить физическое соединение с источником данных. Метод возвращает объект базового соединения, который может быть использован задачей. Поскольку диспетчер соединений изолирует сведения об объекте базового соединения от задачи, задача должна лишь вызвать метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A>, чтобы установить соединение; при этом нет необходимости заботиться о других аспектах соединения.  
  
## <a name="example"></a>Пример  
 В следующем образце кода демонстрируется проверка имени <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> в методах Validate и Execute, а также показано, как использовать метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A>, чтобы установить физическое соединение в методе Execute.  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;соединений&#41; SSIS](../../connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](../../create-connection-managers.md)  
  
  
