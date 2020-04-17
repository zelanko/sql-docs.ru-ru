---
title: Объект SqlContext Документы Майкрософт
description: При вызове управляемого кода в s'L Server в пользовательском соединении доступ к контексту вызывающего абонента абстрагируется в объекте SqlContext.
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
ms.openlocfilehash: cd6d3091b155ae829e368bdd182b3da8286c7194
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487543"
---
# <a name="sqlcontext-object"></a>Объект SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  На сервере управляемый код запускается при вызове процедуры, функции или метода для определяемого пользователем типа данных CLR или когда действие вызывает срабатывание триггера, определенного на одном из языков платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Так как выполнение этого кода необходимо как часть соединения пользователя, требуется доступ к контексту участника из кода, работающего на сервере. Кроме того, определенные операции доступа к данным могут быть допустимы, только если они выполняются в контексте участника. Например, доступ к вставленным или удаленным псевдотаблицам, применяемым в операциях триггеров, допустим только в контексте участника.  
  
 Контекст вызывающего абонента абстрагируется в объекте **SqlContext.** Для получения дополнительной информации о методах и **свойствах SqlTriggerContext** можно ознакомиться на справочной [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] документации класса **Microsoft.SqlServerContext** в SDK.  
  
 **SqlContext** предоставляет доступ к следующим компонентам:  
  
-   **SqlPipe**: Объект **SqlPipe** представляет собой "трубу", через которую результаты поступают к клиенту. Для получения дополнительной информации об [SqlPipe Object](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)объекте **SqlPipe** см.  
  
-   **SqlTriggerContext**: Объект **SqlTriggerContext** может быть извлечен только из триггера CLR. Он предоставляет сведения об операции, которая вызвала срабатывание триггера, а также карту столбцов, которые были обновлены. Для получения дополнительной информации об объекте **SqlTriggerContext** [см.](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
  
-   **Доступно:** Свойство **IsAvailable** используется для определения доступности контекста.  
  
-   **WindowsIdentity**: Свойство **WindowsIdentity** используется для получения идентификации абонента Windows.  
  
## <a name="determining-context-availability"></a>Определение доступности контекста  
 Запрос класса **SqlContext,** чтобы узнать, работает ли в процессе выполнения в настоящее время код. Для этого проверьте **доступное** свойство объекта **SqlContext.** Свойство **IsAvailable** читается только и возвращается, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] код вызова работает внутри и если другие участники **SlContext** могут быть доступны. **True** Если свойство **IsAvailable** возвращает **сярвые,** все остальные участники **SlContext** бросают **InvalidOperationException,** если используется. Если **IsAvailable** возвращает **false,** любая попытка открыть объект соединения, который имеет "контекстное соединение" в строке соединения, завершается неудачей.  
  
## <a name="retrieving-windows-identity"></a>Извлечение удостоверения Windows  
 Код CLR, выполняющийся внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], всегда запускается в контексте учетной записи процесса. Если код должен выполнять определенные действия, используя личность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя вызова, а не идентификацию процесса, то то же токен олицетворения должен быть получен через свойство **WindowsIdentity** объекта **SqlContext.** Свойство **WindowsIdentity** возвращает экземпляр **WindowsIdentity,** представляющий идентификацию абонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, или аннулировал, если клиент был проверен с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аутентификации. Доступ к этому свойству могут получить только собрания, отмеченные **разрешениями EXTERNAL_ACCESS** или **UNSAFE.**  
  
 После получения объекта **WindowsIdentity** абоненты могут выдавать себя за клиентскую учетную запись и выполнять действия от их имени.  
  
 Личность вызывающего абонента доступна только через **SqlContext.WindowsIdentity,** если клиент, инициировавивший выполнение сохраненной процедуры или функции, подключенной к серверу с помощью аутентификации Windows. Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство имеет значение NULL, а код не может олицетворять участника.  
  
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
 [Объект SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
