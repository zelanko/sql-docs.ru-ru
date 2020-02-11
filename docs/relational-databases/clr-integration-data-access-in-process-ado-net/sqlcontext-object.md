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
ms.openlocfilehash: 746ce8cec228b6fe9a9d36c4e0287ad7c2f3c517
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67951676"
---
# <a name="sqlcontext-object"></a>Объект SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  На сервере управляемый код запускается при вызове процедуры, функции или метода для определяемого пользователем типа данных CLR или когда действие вызывает срабатывание триггера, определенного на одном из языков платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Так как выполнение этого кода необходимо как часть соединения пользователя, требуется доступ к контексту участника из кода, работающего на сервере. Кроме того, определенные операции доступа к данным могут быть допустимы, только если они выполняются в контексте участника. Например, доступ к вставленным или удаленным псевдотаблицам, применяемым в операциях триггеров, допустим только в контексте участника.  
  
 Контекст вызывающего объекта является абстрактным в объекте **SqlContext** . Дополнительные сведения о методах и свойствах **SqlTriggerContext** см. в справочной документации по классу **Microsoft. SqlServer. Server. SqlTriggerContext** в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] пакете SDK.  
  
 **SqlContext** предоставляет доступ к следующим компонентам:  
  
-   **SqlPipe**: объект **SqlPipe** представляет "pipe", через который результаты поступают клиенту. Дополнительные сведения об объекте **SqlPipe** см. в разделе [объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: объект **SqlTriggerContext** может быть получен только из триггера CLR. Он предоставляет сведения об операции, которая вызвала срабатывание триггера, а также карту столбцов, которые были обновлены. Дополнительные сведения об объекте **SqlTriggerContext** см. в разделе [объект SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **Доступно**. свойство **Available** используется для определения доступности контекста.  
  
-   **WindowsIdentity**: свойство **WindowsIdentity** используется для получения удостоверения Windows вызывающего объекта.  
  
## <a name="determining-context-availability"></a>Определение доступности контекста  
 Выполните запрос к классу **SqlContext** , чтобы узнать, выполняется ли выполняющийся в процессе код. Для этого проверьте свойство **Available** объекта **SqlContext** . Свойство **Available** доступно только для чтения и возвращает **значение true** , если вызывающий код выполняется внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и если доступ к другим членам **SqlContext** возможен. Если свойство **Available** возвращает **значение false**, все остальные члены **SqlContext** создают исключение **InvalidOperationException**, если оно используется. Если **функция** IsTrue возвращает **значение false**, то любая попытка открыть объект соединения, в строке соединения которого задано контекстное соединение = true, завершается ошибкой.  
  
## <a name="retrieving-windows-identity"></a>Извлечение удостоверения Windows  
 Код CLR, выполняющийся внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], всегда запускается в контексте учетной записи процесса. Если код должен выполнять определенные действия, используя удостоверение вызывающего пользователя, а не удостоверение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процесса, то токен олицетворения должен быть получен через свойство **WindowsIdentity** объекта **SqlContext** . Свойство **WindowsIdentity** возвращает экземпляр **WindowsIdentity** , представляющий удостоверение [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows вызывающего объекта, или значение null, если клиент прошел проверку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подлинности. Доступ к этому свойству имеют только сборки, помеченные как **EXTERNAL_ACCESSные** , так и **ненадежные** разрешения.  
  
 После получения объекта **WindowsIdentity** вызывающие объекты могут олицетворять учетную запись клиента и выполнять действия от их имени.  
  
 Удостоверение вызывающего объекта доступно только через **SqlContext. WindowsIdentity** , если клиент, который инициировал выполнение хранимой процедуры или функции, подключен к серверу с использованием проверки подлинности Windows. Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство имеет значение NULL, а код не может олицетворять участника.  
  
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
  
  
