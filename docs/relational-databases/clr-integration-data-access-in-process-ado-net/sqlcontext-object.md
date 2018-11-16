---
title: Объект SqlContext | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3293cbed44cc6eeae12c3c48247de8748ddad894
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664874"
---
# <a name="sqlcontext-object"></a>Объект SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  На сервере управляемый код запускается при вызове процедуры, функции или метода для определяемого пользователем типа данных CLR или когда действие вызывает срабатывание триггера, определенного на одном из языков платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Так как выполнение этого кода необходимо как часть соединения пользователя, требуется доступ к контексту участника из кода, работающего на сервере. Кроме того, определенные операции доступа к данным могут быть допустимы, только если они выполняются в контексте участника. Например, доступ к вставленным или удаленным псевдотаблицам, применяемым в операциях триггеров, допустим только в контексте участника.  
  
 Контекст вызывающего является абстрактным в **SqlContext** объекта. Дополнительные сведения о **SqlTriggerContext** методы и свойства, см. в разделе **Microsoft.SqlServer.Server.SqlTriggerContext** справочной документации по [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
 **SqlContext** предоставляет доступ к следующим компонентам:  
  
-   **SqlPipe**: **SqlPipe** объект представляет «канал», по которому результаты передаются клиенту. Дополнительные сведения о **SqlPipe** объекта, см. в разделе [объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: **SqlTriggerContext** объекта можно получить только из триггера CLR. Он предоставляет сведения об операции, которая вызвала срабатывание триггера, а также карту столбцов, которые были обновлены. Дополнительные сведения о **SqlTriggerContext** объекта, см. в разделе [SqlTriggerContext, объект](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **IsAvailable**: **IsAvailable** свойство используется для определения доступности контекста.  
  
-   **WindowsIdentity**: **WindowsIdentity** свойство используется для получения удостоверения Windows вызывающего объекта.  
  
## <a name="determining-context-availability"></a>Определение доступности контекста  
 Запрос **SqlContext** класса, чтобы увидеть, если текущий выполняемый код выполняется в процессе. Чтобы сделать это, проверьте **IsAvailable** свойство **SqlContext** объекта. **IsAvailable** свойство только для чтения и возвращает **True** Если вызывающий код выполняется внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и если другие **SqlContext** членам можно получить доступ. Если **IsAvailable** возвращает **False**, все остальные **SqlContext** вызывать члены **InvalidOperationException**, если используется . Если **IsAvailable** возвращает **False**, любая попытка открыть объект соединения с «контекстное соединение = true» в строке подключения завершается ошибкой.  
  
## <a name="retrieving-windows-identity"></a>Извлечение удостоверения Windows  
 Код CLR, выполняющийся внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], всегда запускается в контексте учетной записи процесса. Если код должен выполнить определенные действия с использованием удостоверения вызывающего пользователя, а не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификация процесса, а затем необходимо получить маркер олицетворения при помощи **WindowsIdentity** свойство  **SqlContext** объекта. **WindowsIdentity** возвращает **WindowsIdentity** экземпляр который представляет [!INCLUDE[msCoName](../../includes/msconame-md.md)] удостоверение Windows вызывающего объекта, или значение null, если клиент прошел проверку подлинности с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. Только сборки, имеющие **EXTERNAL_ACCESS** или **UNSAFE** разрешений можно получить доступ к этому свойству.  
  
 После получения **WindowsIdentity** объекта, вызывающие объекты могут олицетворять учетную запись клиента и выполнять действия от их имени.  
  
 Удостоверение вызывающего доступно только через **SqlContext.WindowsIdentity** Если инициировавший выполнение хранимой процедуры или функции клиент подключен к серверу с помощью проверки подлинности Windows. Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство имеет значение NULL, а код не может олицетворять участника.  
  
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
  
## <a name="see-also"></a>См. также  
 [Объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [Объект SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
