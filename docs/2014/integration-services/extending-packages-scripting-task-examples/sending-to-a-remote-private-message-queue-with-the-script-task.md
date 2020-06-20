---
title: Отправка в удаленную закрытую очередь сообщений в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 39ccf68bcd7a16c95fd5247c7b7a9fa7b5e63fce
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966464"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»
  Служба очередей сообщений (называемая также MSMQ) облегчает разработчикам обеспечение быстрой и надежной связи с прикладными программами при помощи отправки и получения сообщений. Очередь сообщений может находиться в локальном или в удаленном компьютере и может быть открытой или закрытой. В службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] диспетчер соединений MSMQ и задача «Очередь сообщений» не поддерживают отправку в закрытую очередь на удаленном компьютере. Но при использовании задачи «Скрипт» можно легко отправить сообщение в удаленную закрытую очередь.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 В следующем примере для отправки текста (содержащегося в переменной пакета) в удаленную закрытую очередь сообщений используется существующий диспетчер соединений MSMQ вместе с объектами и методами из пространства имен System.Messaging. Вызов метода М:Микрософт.склсервер.ДТС.манажедконнектионс.мсмкконн.аккуиреконнектион (System. Object) диспетчера соединений MSMQ возвращает объект **MessageQueue** , метод которого выполняет `Send` эту задачу.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Создайте диспетчер соединений MSMQ с именем по умолчанию. Установите путь к допустимой удаленной закрытой очереди в следующем формате:  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Создайте [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переменную с именем **MessageText** типа `String` , чтобы передать текст сообщения в скрипт. Введите сообщение по умолчанию как значение переменной.  
  
3.  Добавьте задачу «Скрипт» в область конструктора и измените ее. На вкладке **Скрипт** **редактора задачи "Скрипт"** добавьте переменную `MessageText` к свойству **ReadOnlyVariables**, чтобы сделать переменную доступной в скрипте.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA).  
  
5.  В проект скрипта добавьте ссылку на пространство имен `System.Messaging`.  
  
6.  Замените содержимое окна скрипта кодом из следующего раздела.  
  
## <a name="code"></a>Код  
  
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
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Message Queue Task](../control-flow/message-queue-task.md)  
  
  
