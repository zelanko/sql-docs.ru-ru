---
title: "Объект SqlContext | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
caps.latest.revision: "54"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4837e53e3642c1ed0fe5c5b8fa218e8f8a890651
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqlcontext-object"></a>Объект SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Вызов управляемого кода на сервере, при вызове процедуры или функции, при вызове метода для среды выполнения (CLR) определяемых пользователем тип или действие вызывает срабатывание триггера, определенного на любой из [!INCLUDE[msCoName](../../includes/msconame-md.md)] языки платформы .NET Framework. Так как выполнение этого кода необходимо как часть соединения пользователя, требуется доступ к контексту участника из кода, работающего на сервере. Кроме того, определенные операции доступа к данным могут быть допустимы, только если они выполняются в контексте участника. Например, доступ к вставленным или удаленным псевдотаблицам, применяемым в операциях триггеров, допустим только в контексте участника.  
  
 Контекст участника извлекается из **SqlContext** объекта. Дополнительные сведения о **SqlTriggerContext** методы и свойства, в разделе **Microsoft.SqlServer.Server.SqlTriggerContext** справочной документации [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
 **SqlContext** предоставляет доступ к следующие компоненты:  
  
-   **SqlPipe**: **SqlPipe** объект представляет «канал», по которому результаты передаются клиенту. Дополнительные сведения о **SqlPipe** см. в разделе [объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: **SqlTriggerContext** объекта можно получить только из триггера CLR. Он предоставляет сведения об операции, которая вызвала срабатывание триггера, а также карту столбцов, которые были обновлены. Дополнительные сведения о **SqlTriggerContext** см. в разделе [SqlTriggerContext, объект](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **IsAvailable**: **IsAvailable** свойство используется для определения доступности контекста.  
  
-   **WindowsIdentity**: **WindowsIdentity** свойство используется для получения удостоверения Windows участника.  
  
## <a name="determining-context-availability"></a>Определение доступности контекста  
 Запрос **SqlContext** класс, чтобы проверить, установлена ли код выполняться в данный момент в процессе. Чтобы сделать это, проверьте **IsAvailable** свойство **SqlContext** объекта. **IsAvailable** свойство доступно только для чтения и возвращает **True** Если вызывающий код выполняется внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и если другие **SqlContext** членам можно получить доступ. Если **IsAvailable** возвращает **False**, все остальные **SqlContext** вызывать члены **InvalidOperationException**, если используется . Если **IsAvailable** возвращает **False**, любая попытка открыть объект соединения, имеющий» контекстного соединения = true» в строке подключения завершается ошибкой.  
  
## <a name="retrieving-windows-identity"></a>Извлечение удостоверения Windows  
 Код CLR, выполняющийся внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], всегда запускается в контексте учетной записи процесса. Если код должен выполнить определенные действия с использованием удостоверения вызывающего пользователя, а не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификации, процесса, а затем маркер олицетворения должен быть получен с помощью **WindowsIdentity** свойство  **SqlContext** объекта. **WindowsIdentity** возвращает **WindowsIdentity** представляет экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] удостоверение Windows вызывающего объекта, или значение null, если клиент прошел проверку подлинности с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. Только сборки, имеющие **EXTERNAL_ACCESS** или **UNSAFE** разрешений можно получить доступ к этому свойству.  
  
 После получения **WindowsIdentity** объекта, вызывающие могут олицетворять учетную запись клиента и выполнять действия от их имени.  
  
 Удостоверение вызывающей стороны возможен только посредством **SqlContext.WindowsIdentity** Если клиентом, который инициировал выполнение хранимой процедуры или функции, подключенных к серверу, используя проверку подлинности Windows. Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство имеет значение NULL, а код не может олицетворять участника.  
  
### <a name="example"></a>Пример  
 В следующем примере показано, как получить удостоверение Windows вызывающего клиента и олицетворить этого клиента.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [SqlTriggerContext, объект](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [Триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
