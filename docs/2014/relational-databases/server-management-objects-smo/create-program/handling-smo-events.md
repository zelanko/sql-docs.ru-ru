---
title: Обработка событий SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0d309103880a369a88952e19b252fc15693fdd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191919"
---
# <a name="handling-smo-events"></a>Обработка событий SMO
  На некоторые типы событий сервера можно подписаться с помощью обработчика событий и объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
 Многие классы экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) могут инициировать события при выполнении на сервере определенных действий.  
  
 Эти события можно обрабатывать программно, если установить обработчик события и подписаться на связанные события. Этот тип обработки событий является переходным, поскольку все подписки удаляются при завершении клиентской программы SMO.  
  
## <a name="connectioncontext-event-handling"></a>Обработка события ConnectionContext  
 Объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> поддерживает несколько типов событий. Свойство события необходимо задать равным экземпляру соответствующего обработчика события, а объект обработчика события следует определить как защищенную функцию, обрабатывающую событие.  
  
## <a name="event-subscription"></a>Подписка на событие  
 Для обработки некоторого события пишется класс обработчика этого события, создается его экземпляр, этот обработчик события назначается родительскому объекту, затем производится подписка на данное событие.  
  
 Для обработки событий необходимо написать класс обработчика события. Класс обработчика события может содержать более одной функции обработки события, и его надо установить для обрабатываемых событий. Функции обработчика события получают информацию о событии из *ServerEventNotificatificationArgs* параметр, который может использоваться для передачи сведений о событии.  
  
 Типы событий базы данных и сервера, которые могут быть обработаны, перечислены в <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> класс и <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>класса.  
  
## <a name="example"></a>Пример  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a>Регистрация обработчиков событий и подписка на обработку событий на языке Visual Basic  
 Данный пример кода показывает, как установить обработчик события и подписаться на события базы данных.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a>Регистрация обработчиков событий и подписка на обработку событий на языке Visual C#  
 Данный пример кода показывает, как установить обработчик события и подписаться на события базы данных.  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
