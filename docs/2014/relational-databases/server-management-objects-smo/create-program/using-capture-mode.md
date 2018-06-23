---
title: Режим захвата с помощью | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0585f571868c88b6fda1926b03f34f5e131bf6c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109671"
---
# <a name="using-capture-mode"></a>Использование режима записи
  Программы SMO могут фиксировать и записывать эквивалентные инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] вместо исполняемых программой инструкций или в дополнение к ним. Режим записи можно включить с помощью объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection> или свойства <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
## <a name="example"></a>Пример  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="enabling-capture-mode-in-visual-basic"></a>Включение режима записи в языке Visual Basic  
 В данном примере программного кода включается режим записи, а затем выводятся зафиксированные команды [!INCLUDE[tsql](../../../includes/tsql-md.md)], содержащиеся в буфере записи.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCapture1](SMO How to#SMO_VBCapture1)]  -->  
  
## <a name="enabling-capture-mode-in-visual-c"></a>Включение режима записи в языке Visual C#  
 В данном примере программного кода включается режим записи, а затем выводятся зафиксированные команды [!INCLUDE[tsql](../../../includes/tsql-md.md)], содержащиеся в буфере записи.  
  
```  
{   
// Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
// Set the execution mode to CaptureSql for the connection.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql;   
// Make a modification to the server that is to be captured.   
srv.UserOptions.AnsiNulls = true;   
srv.Alter();   
// Iterate through the strings in the capture buffer and display the captured statements.   
string s;   
foreach ( String p_s in srv.ConnectionContext.CapturedSql.Text ) {   
   Console.WriteLine(p_s);   
}   
// Execute the captured statements.   
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text);   
// Revert to immediate execution mode.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
  