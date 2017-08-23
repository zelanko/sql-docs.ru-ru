---
title: "Ведение журналов в задаче «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98859dafe0b023954f10239fe11e8b76f36ab28b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-task"></a>Ведение журнала в задаче «Скрипт»
  Ведение журнала в пакетах служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] позволяет записывать для последующего анализа извлекаемую из стандартных событий или определяемых пользователем сообщений подробную информацию о ходе выполнения, полученных результатах и возникших проблемах. Можно использовать задачу «скрипт» <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> метод **Dts** для записи в журнал определяемых пользователем данных. Если включено ведение журнала и **ScriptTaskLogEntry** событие выбирается для регистрации **сведения** вкладке **Настройка журналов служб SSIS** диалоговое окно, в рамках одного вызова <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> метод сохраняет сведения о событии в все регистраторы, настроенных для данной задачи.  
  
> [!NOTE]  
>  Хотя журнал можно вести непосредственно из задачи «Скрипт», можно реализовать события вместо ведения журнала. При использовании событий можно не только включить запись в журнал сообщений о событиях, но и реагировать на события с помощью обработчиков событий, определяемых пользователем или заданных по умолчанию.  
  
 Дополнительные сведения о ведении журнала см. в разделе [службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="logging-example"></a>Пример ведения журнала  
 Следующий пример иллюстрирует ведение журнала из задачи «Скрипт» путем записи в журнал значения, представляющего число обработанных строк.  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [ведение журнала пользовательских событий для задач служб Integration Services](http://go.microsoft.com/fwlink/?LinkId=165644), на сайте dougbert.com  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
