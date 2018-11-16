---
title: Вызов событий в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c5c5590bb6bdeb9539fb42e4c17b8ea38c5c85f
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641741"
---
# <a name="raising-events-in-the-script-task"></a>Вызов событий в задаче «Скрипт»
  События позволяют сообщать об ошибках и предупреждениях, а также передавать другие сведения, например о ходе выполнения задачи или ее состоянии, в пакет, содержащий задачу. Пакет предоставляет обработчики событий для управления уведомлениями о событиях. Задача "Скрипт" может создавать события, вызывая методы свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> объекта **Dts**. Дополнительные сведения о том, как пакеты службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] обрабатывают события, см. в разделе [Обработчики событий в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-event-handlers.md).  
  
 События могут регистрироваться любым регистратором, включенным в пакете. Регистраторы сохраняют сведения о событиях в хранилище данных. Задача «Скрипт» может также использовать метод <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> для занесения записей в регистратор без вызова событий. Дополнительные сведения об использовании метода <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> см. в разделе [Ведение журналов в задаче "Скрипт"](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md).  
  
 Для вызова события задача «Скрипт» вызывает один из методов, предоставляемых свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>. В следующей таблице перечислены методы, предоставляемые свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
|Событие|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|Вызывает в пакете определяемое пользователем событие.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|Извещает пакет об ошибке.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|Передает сведения пользователю.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|Информирует пакет о ходе выполнения задачи.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|Возвращает значение, которое указывает, нужно ли пакету, чтобы задача преждевременно прервала выполнение.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|Информирует пакет, что задача находится в состоянии, которое требует уведомить пользователя, но не является состоянием ошибки.|  
  
## <a name="events-example"></a>Пример события  
 В следующем примере демонстрируется вызов событий изнутри задачи «Скрипт». Пример использует собственную функцию API Windows, чтобы определить, доступно ли соединение с Интернетом. Если соединения нет, создается ошибка. Если используется потенциально нестабильное соединение по модему, пример формирует предупреждение. В противном случае возвращается информационное сообщение, что соединение с Интернетом обнаружено.  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Обработчики событий в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Добавление обработчика событий к пакету](https://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
