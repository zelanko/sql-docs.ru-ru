---
title: Написание кода пользовательского диспетчера соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e11738fb33c45bf1d18b32bb4e3b1be4d0cf6b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62768919"
---
# <a name="coding-a-custom-connection-manager"></a>Написание кода пользовательского диспетчера соединений
  После создания класса, наследующего от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, и применения к нему атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>, необходимо переопределить реализацию свойств и методов базового класса, чтобы обеспечить пользовательские функциональные возможности.  
  
 Примеры пользовательских диспетчеров соединений см. в разделе [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](developing-a-user-interface-for-a-custom-connection-manager.md). Примеры кода, приведенные в этом разделе, взяты из образца пользовательского диспетчера соединений SQL Server.  
  
> [!NOTE]  
>  Большая часть задач, источников и назначений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] работает только с определенными типами встроенных диспетчеров соединений. Поэтому данные образцы нельзя протестировать с помощью встроенных задач и компонентов.  
  
## <a name="configuring-the-connection-manager"></a>Настройка диспетчера соединений  
  
### <a name="setting-the-connectionstring-property"></a>Задание свойства ConnectionString  
 Свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> – важное свойство, которое является единственным уникальным свойством для пользовательского диспетчера соединений. Диспетчер соединений использует значение этого свойства для соединения с внешним источником данных. Если необходимо скомбинировать несколько других свойств, например, имя сервера и имя базы данных, чтобы создать строку соединения, можно использовать вспомогательную функцию для сборки строки путем замены определенных значений в шаблоне строки соединения новыми значениями, предоставленными пользователем. В следующем примере кода демонстрируется реализация свойства <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A>, которое использует вспомогательную функцию для сборки строки.  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a>Проверка диспетчера соединений  
 Необходимо переопределить метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>, чтобы убедиться в правильности настройки диспетчера соединений. Как минимум, следует проверить формат строки соединения и убедиться в том, что предоставлены значения для всех аргументов. Выполнение не может продолжиться, пока диспетчер соединений не возвратит значение <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> из метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>.  
  
 В следующем примере кода демонстрируется реализация метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>, который проверяет, указано ли пользователем имя сервера для соединения.  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a>Сохраняемость диспетчера соединений  
 Как правило, реализовывать пользовательскую сохраняемость для диспетчера соединений нет необходимости. Нестандартный механизм сохраняемости необходим только в случае, когда свойства объекта используют сложные типы данных. Дополнительные сведения см. в разделе [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md).  
  
## <a name="working-with-the-external-data-source"></a>Работа с внешним источником данных  
 Методы, поддерживающие соединение с внешним источником данных, являются наиболее важными методами для пользовательского диспетчера соединений. Методы <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> вызываются в различные моменты, как во время разработки, так и во время выполнения.  
  
### <a name="acquiring-the-connection"></a>Получение соединения  
 Необходимо решить, какого типа объект должен возвращаться методом <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> из пользовательского диспетчера соединений. Например, диспетчер соединения файлов возвращает только строку, содержащую путь и имя файла, в то время как диспетчер соединений ADO.NET возвращает управляемый объект соединения, который уже открыт. Диспетчер соединений OLE DB возвращает собственный объект соединения OLE DB, который не может использоваться из управляемого кода. Пользовательский диспетчер соединений SQL Server, из которого взяты фрагменты кода в этом разделе, возвращает открытый объект `SqlConnection`.  
  
 Пользователям диспетчера соединений необходимо знать заранее, какого типа объект следует ожидать, чтобы они могли привести возвращенный объект к соответствующему типу и получить доступ к его методам и свойствам.  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a>Освобождение соединения  
 Действие, которое необходимо предпринять в методе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>, зависит от типа объекта, возвращаемого из метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>. Если имеется открытый объект соединения, следует закрыть его и освободить используемые им ресурсы. Если методом <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> возвращено только строковое значение, не нужно предпринимать никаких действий.  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского диспетчера соединений](creating-a-custom-connection-manager.md)   
 [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
