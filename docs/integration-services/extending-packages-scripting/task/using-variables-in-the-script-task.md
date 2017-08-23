---
title: "Использование переменных в задаче «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ccfd7ce8e8f53d12dac3b021d5f62bd03947413d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-task"></a>Использование переменных в задаче «Скрипт»
  Переменные позволяют задаче «Скрипт» обмениваться данными с другими объектами в пакете. Дополнительные сведения см. в разделе [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 Задача «скрипт» использует <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> свойство **Dts** объект для чтения и записи к <xref:Microsoft.SqlServer.Dts.Runtime.Variable> объекты в пакете.  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> Свойство <xref:Microsoft.SqlServer.Dts.Runtime.Variable> класс относится к типу **объекта**. Поскольку в задаче «скрипт» **Option Strict** включен, необходимо привести <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> свойство к соответствующему типу, прежде чем использовать его.  
  
 Добавить существующие переменные к <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> перечислены в **редактор задачи «скрипт»** чтобы сделать их доступными для пользовательского скрипта. Помните, что в именах переменных учитывается регистр. В сценарии, можно получить доступ к переменным обоих типов с помощью <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> свойство **Dts** объекта. Используйте **значение** свойство для чтения и записи в отдельные переменные. Задача «Скрипт» обеспечивает прозрачное для пользователя управление блокировкой во время считывания и изменение значений переменных в скрипте.  
  
 Чтобы проверить наличие переменной перед ее использованием в коде, можно использовать метод <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Variables>, возвращенной свойством <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 Можно также использовать <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> свойство (Dts.VariableDispenser) для работы с переменными в задаче «скрипт». При использовании свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> необходимо обрабатывать в коде и семантику блокирования, и приведение типов данных для значений переменных. Может потребоваться использовать свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> вместо свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>, если возникает необходимость работать с переменной, недоступной во время разработки, но создаваемой программным путем во время выполнения.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Использование задачи «Скрипт» в контейнере «цикл по каждому элементу»  
 Если задача «Скрипт» неоднократно запускается в контейнере «цикл по каждому элементу», то в скрипте обычно требуется обеспечить работу с содержимым текущего элемента в перечислителе. Например, при использовании перечислителя с циклом по каждому файлу в скрипте требуется определить имя текущего файла, а при использовании перечислителя ADO по каждой строке в скрипте необходимо получать содержимое столбцов в текущей строке данных.  
  
 Переменные делают возможной такую связь между контейнером «цикл по каждому элементу» и задачей «Скрипт». На **сопоставления переменной** страница **Редактор циклов по каждому элементу**, переменные назначить каждый элемент данных, возвращаемый одним перечисленным элементом. Например, перечислитель с циклом по каждому файлу возвращает только имя файла из позиции с индексом 0 и поэтому требует сопоставления лишь с одной переменной, а перечислитель, который возвращает несколько столбцов данных из каждой строки, требует сопоставить отдельную переменную с каждым столбцом, предназначенным для использования в задаче «Скрипт».  
  
 После сопоставления перечисленных элементов для переменных, то необходимо добавить сопоставленные переменные к **ReadOnlyVariables** свойство **сценарий** страница **редактор задачи «скрипт»** чтобы сделать их доступными для скрипта. Пример задачи «скрипт» в контейнере цикл, который обрабатывает файлы изображений в папку, в разделе [работа с образами с помощью задачи «скрипт»](../../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Пример использования переменных  
 В следующем примере показано, как получить доступ и использовать переменные в задаче «Скрипт», чтобы определить пути рабочего процесса пакета. В образце предполагается, что вы создали целочисленных переменных с именем `CustomerCount` и `MaxRecordCount` и добавлены к **ReadOnlyVariables** коллекции в **редактор задачи «скрипт»**. Переменная `CustomerCount` содержит количество записей с данными заказчиков, которые должны быть импортированы. Если это значение больше значения `MaxRecordCount`, задача «Скрипт» сообщает о неудачном завершении. Если неудачное завершение возникает из-за превышения порогового значения `MaxRecordCount`, в пути обработки ошибок рабочего процесса можно реализовать все необходимые операции очистки.  
  
 Чтобы успешно откомпилировать этот образец, необходимо добавить ссылку на сборку Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
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
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Переменные](../../../integration-services/integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
