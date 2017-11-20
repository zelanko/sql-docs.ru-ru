---
title: "Отслеживание счетчиков производительности с помощью задачи «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: fd733f7d2fdf9c5d1181df6e7856d729e9a58026
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="monitoring-performance-counters-with-the-script-task"></a>Наблюдение за счетчиками производительности в задаче «Скрипт»
  Администраторам необходимо наблюдать за производительностью пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], выполняющих сложные преобразования больших объемов данных. **System.Diagnostics** пространство имен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предоставляет классы для использования существующих счетчиков производительности, а также для создания собственных счетчиков производительности.  
  
 Счетчики производительности хранят сведения о производительности приложения, которые можно использовать для анализа производительности программного обеспечения по времени. Счетчики производительности можно отслеживать локально или удаленно с помощью **монитора производительности** средства. Значения счетчиков производительности можно сохранить в переменных, чтобы далее в пакете можно было организовать ветвление потока управления.  
  
 В качестве альтернативы с помощью счетчиков производительности можно увеличить <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> события с помощью <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> свойство **Dts** объекта. Событие <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> возвращает среде выполнения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] как сведения о добавочном ходе выполнения, так и процент завершения задачи.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Следующий пример создает пользовательский счетчик производительности и увеличивает его значение. Во-первых, пример определяет, существует ли счетчик производительности. Если счетчик производительности, который не будет создана, скрипт вызывает **создать** метод **категории счетчика производительности** для его создания. После создания счетчика производительности скрипт увеличивает его значение. Наконец, пример следует рекомендациям и вызову метода **закрыть** метод для счетчика производительности, когда он больше не нужен.  
  
> [!NOTE]  
>  Чтобы создать новую категорию счетчика производительности и сам счетчик производительности, необходимы права администратора. Кроме того, новая категория и счетчик производительности после создания сохраняются на компьютере.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
-   Используйте **Imports** инструкции в коде для импорта **System.Diagnostics** пространства имен.  
  
### <a name="example-code"></a>Пример кода  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  

