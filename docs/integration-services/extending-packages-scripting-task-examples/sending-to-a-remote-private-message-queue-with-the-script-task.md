---
title: "Отправка в удаленную закрытую очередь сообщений с помощью задачи «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5ab9314ef0825486914d1801bfa2b9613883b43e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»
  Служба очередей сообщений (называемая также MSMQ) облегчает разработчикам обеспечение быстрой и надежной связи с прикладными программами при помощи отправки и получения сообщений. Очередь сообщений может находиться в локальном или в удаленном компьютере и может быть открытой или закрытой. В службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] диспетчер соединений MSMQ и задача «Очередь сообщений» не поддерживают отправку в закрытую очередь на удаленном компьютере. Но при использовании задачи «Скрипт» можно легко отправить сообщение в удаленную закрытую очередь.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 В следующем примере существующий диспетчер соединений MSMQ, а также объекты и методы из пространства имен System.Messaging для отправки текста, содержащегося в переменной пакета в удаленную закрытую очередь сообщений. Вызов метода M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) диспетчера соединений MSMQ возвращает **MessageQueue** которого **отправки** метод выполняет эту задачу.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Создайте диспетчер соединений MSMQ с именем по умолчанию. Установите путь к допустимой удаленной закрытой очереди в следующем формате:  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Создание [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переменную с именем **MessageText** типа **строка** чтобы передать текст сообщения в скрипт. Введите сообщение по умолчанию как значение переменной.  
  
3.  Добавьте задачу «Скрипт» в область конструктора и измените ее. На **сценарий** вкладке **редактор задачи «скрипт»**, добавьте `MessageText` переменной **ReadOnlyVariables** свойство, чтобы сделать переменную доступной в скрипте .  
  
4.  Нажмите кнопку **изменить скрипт** Открытие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA) Редактор сценариев.  
  
5.  Добавьте ссылку в проект скрипта **System.Messaging** пространства имен.  
  
6.  Замените содержимое окна скрипта кодом из следующего раздела.  
  
## <a name="code"></a>код  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Задача «Очередь сообщений»](../../integration-services/control-flow/message-queue-task.md)  
  
  

