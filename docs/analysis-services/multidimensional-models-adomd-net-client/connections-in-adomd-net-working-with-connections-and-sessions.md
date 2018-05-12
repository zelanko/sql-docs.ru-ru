---
title: Работа с соединениями и сеансами в ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b5339778e1491259f5349355e80890e1cfee8f9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="connections-in-adomdnet---working-with-connections-and-sessions"></a>Connections in ADOMD.NET — работа с соединениями и сеансами
  В XML для аналитики (XMLA) сеансы обеспечивают поддержку операций с сохранением состояния при доступе к аналитическим данным. Сеансы образуют область и контекст команд и транзакций для источника аналитических данных. Используемые для управления сеансами элементы XMLA — [BeginSession](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md), [Session](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)и [EndSession](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md).  
  
 Компонент ADOMD.NET использует эти три элемента XMLA для работы с сеансами при запуске сеанса, выполнении запросов или получении данных во время сеанса, а также при его закрытии.  
  
## <a name="starting-a-session"></a>Запуск сеанса  
 Свойство <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> содержит идентификатор активного сеанса, связанного с объектом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Правильно пользуясь этим свойством, можно эффективно управлять поддержкой состояния клиента и сервера в приложении.  
  
-   Если свойству <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> не задан допустимый идентификатор сеанса при вызове метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A>, объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> запрашивает у поставщика новый идентификатор сеанса. Компонент ADOMD.NET инициирует сеанс, отправляя поставщику заголовок XMLA **BeginSession** . Если попытка компонента ADOMD.NET запустить сеанс завершилась успешно, то ADOMD.NET устанавливает значение свойства <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>, равное идентификатору только что созданного сеанса.  
  
-   Если свойство <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> при вызове метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> имеет допустимый идентификатор сеанса, то объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> пытается подключиться к указанному сеансу.  
  
 Если объекту <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> не удается установить соединение с указанным сеансом или если поставщик не поддерживает сеансы, возникает исключение.  
  
> [!NOTE]  
>  После того как компонент ADOMD.NET создал сеанс, к этому единственному активному сеансу можно подключить несколько объектов <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, кроме того, можно также отключить один объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> от этого сеанса и подключить его к другому.  
  
## <a name="working-in-a-session"></a>Работа с сеансом  
 После подключения ADOMD.NET <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> объекта к допустимому сеансу, ADOMD.NET будет отправлять XMLA **сеанса** заголовок для поставщика с каждым запросом данных или метаданных, произведенным приложением. В каждом запросе идентификатору сеанса будет задано значение свойства <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>.  
  
 Наличие идентификатора сеанса не гарантирует того, что сеанс остается допустимым. Если время сеанса истекает (например, если истекло его время ожидания или потеряно соединение), поставщик может завершить и выполнить откат действий, выполнявшихся во время сеанса. В этом случае все последующие вызовы методов, поступающие от объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, будут вызывать исключение. Приложение должно быть в состоянии обрабатывать эти исключения в любой момент при получении данных или метаданных от поставщика, так как они возникают только при отправке поставщику следующего запроса, а не по истечении времени сеанса.  
  
## <a name="closing-a-session"></a>Закрытие сеанса  
 Если <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> метод вызывается без указания значения *endSession* параметра, или если *endSession* параметр имеет значение True, подключение к сеансу и сеанса связанные с <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> закрываются. Чтобы закрыть сеанс, компонент ADOMD.NET отправляет XML для Аналитики **EndSession** заголовок для поставщика с Идентификатором сеанса присвоено значение <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> свойства.  
  
 Если <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> метод вызывается с *endSession* параметра задано значение False, то сеанс, связанный с <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> остается активным, а соединение с этим сеансом закрывается.  
  
## <a name="example-of-managing-a-session"></a>Пример управления сеансом  
 В следующем примере показано, как в ADOMD.NET открывать соединение, создавать сеанс, а также закрывать соединение, не закрывая сам сеанс:  
  
```vb  
Public Function CreateSession(ByVal connectionString As String) As String  
    Dim strSessionID As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' First, try to connect to the specified data source.  
        ' If the connection string is not valid, or if the specified  
        ' provider does not support sessions, an exception is thrown.  
        objConnection.ConnectionString = connectionString  
        objConnection.Open()  
  
        ' Now that the connection is open, retrieve the new  
        ' active session ID.  
        strSessionID = objConnection.SessionID  
        ' Close the connection, but leave the session open.  
        objConnection.Close(False)  
        Return strSessionID  
  
    Finally  
        objConnection = Nothing  
    End Try  
End Function  
```  
  
```csharp  
static string CreateSession(string connectionString)  
{  
    string strSessionID = "";  
    AdomdConnection objConnection = new AdomdConnection();  
    try  
    {  
        /*First, try to connect to the specified data source.  
          If the connection string is not valid, or if the specified  
          provider does not support sessions, an exception is thrown. */  
        objConnection.ConnectionString = connectionString;  
        objConnection.Open();  
  
        // Now that the connection is open, retrieve the new  
        // active session ID.  
        strSessionID = objConnection.SessionID;  
        // Close the connection, but leave the session open.  
        objConnection.Close(false);  
        return strSessionID;  
    }  
    finally  
    {  
        objConnection = null;  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Установление соединений в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
  
