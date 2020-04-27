---
title: Объект SqlContext | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 223111874ca34ba4df4968c550e6cc47edf2b390
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62920047"
---
# <a name="sqlcontext-object"></a>Объект SqlContext
  На сервере управляемый код запускается при вызове процедуры, функции или метода для определяемого пользователем типа данных CLR или когда действие вызывает срабатывание триггера, определенного на одном из языков платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Так как выполнение этого кода необходимо как часть соединения пользователя, требуется доступ к контексту участника из кода, работающего на сервере. Кроме того, определенные операции доступа к данным могут быть допустимы, только если они выполняются в контексте участника. Например, доступ к вставленным или удаленным псевдотаблицам, применяемым в операциях триггеров, допустим только в контексте участника.  
  
 Контекст участника извлекается из объекта `SqlContext`. Дополнительные сведения о методах и свойствах `SqlTriggerContext` см. разделе `Microsoft.SqlServer.Server.SqlTriggerContext` справочной документации по пакету SDK платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 Объект `SqlContext` обеспечивает доступ к следующим компонентам.  
  
-   `SqlPipe`: объект `SqlPipe` представляет "канал", по которому результаты передаются клиенту. Дополнительные сведения об объекте см `SqlPipe` . в разделе [объект SqlPipe](sqlpipe-object.md).  
  
-   `SqlTriggerContext`: объект `SqlTriggerContext` можно получить только из триггера CLR. Он предоставляет сведения об операции, которая вызвала срабатывание триггера, а также карту столбцов, которые были обновлены. Дополнительные сведения об объекте см `SqlTriggerContext` . в разделе [объект SqlTriggerContext](sqltriggercontext-object.md).  
  
-   `IsAvailable`: свойство `IsAvailable` используется для определения доступности контекста.  
  
-   `WindowsIdentity`: свойство `WindowsIdentity` используется для получения удостоверения Windows участника.  
  
## <a name="determining-context-availability"></a>Определение доступности контекста  
 Выполните запрос к классу `SqlContext`, чтобы определить, работает ли выполняемый в данный момент код в процессе. Чтобы сделать это, проверьте свойство `IsAvailable` объекта `SqlContext`. Свойство `IsAvailable` предназначено только для чтения; оно возвращает значение `True`, если вызывающий код выполняется внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также если можно получить доступ к другим членам объекта `SqlContext`. Если свойство `IsAvailable` возвращает значение `False`, все остальные члены `SqlContext`, если они используются, формируют исключение `InvalidOperationException`. Если свойство `IsAvailable` возвращает значение `False`, любая попытка открыть объект соединения, имеющий в строке соединения текст «context connection=true», закончится неудачей.  
  
## <a name="retrieving-windows-identity"></a>Извлечение удостоверения Windows  
 Код CLR, выполняющийся внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], всегда запускается в контексте учетной записи процесса. Если код должен выполнить определенные действия с использованием удостоверения вызывающего пользователя, а не удостоверения процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то необходимо получить токен олицетворения при помощи свойства `WindowsIdentity` объекта `SqlContext`. Свойство `WindowsIdentity` возвращает экземпляр `WindowsIdentity`, представляющий удостоверение [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows участника или значение NULL, если проверка подлинности клиента выполнялась при помощи проверки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Доступ к этому свойству могут получить только сборки, имеющие разрешения `EXTERNAL_ACCESS` или `UNSAFE`.  
  
 Получив объект `WindowsIdentity`, вызывающие могут олицетворять учетную запись клиента и выполнять действия от их имени.  
  
 Если инициировавший выполнение хранимой процедуры или функции клиент соединился с сервером при помощи проверки подлинности Windows, удостоверение участника доступно только через метод `SqlContext.WindowsIdentity`. Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство имеет значение NULL, а код не может олицетворять участника.  
  
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
 [Объект SqlPipe](sqlpipe-object.md)   
 [Объект SqlTriggerContext](sqltriggercontext-object.md)   
 [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [Внутрипроцессные расширения SQL Server для ADO.NET](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
