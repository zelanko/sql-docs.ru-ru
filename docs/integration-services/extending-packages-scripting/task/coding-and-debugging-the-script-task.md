---
title: Написание кода и отладка задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a437704946f379f38aa590ccbf53f240fad94cc
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296920"
---
# <a name="coding-and-debugging-the-script-task"></a>Написание кода и отладка задачи «Скрипт»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После настройки задачи "Скрипт" в окне **Редактор задачи "Скрипт"** нужно создать пользовательский код в среде разработки задачи "Скрипт".  
  
## <a name="script-task-development-environment"></a>Среда разработки задачи «Скрипт»  
 Задача "Скрипт" использует набор средств [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools для работы с приложениями (VSTA) в качестве среды разработки для самого скрипта.  
  
 Код скрипта пишется на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Пользователь указывает язык скрипта, задавая значение свойства **ScriptLanguage** в окне **Редактор задачи "Скрипт"** . Если разработчик предпочитает пользоваться другим языком программирования, можно разработать пользовательскую сборку на выбранном языке и вызвать его функциональные возможности из кода в задаче «Скрипт».  
  
 Скрипт, созданный в задаче «Скрипт», хранится в определении пакета. Отдельного файла скрипта не существует. Поэтому использование задачи «Скрипт» не влияет на развертывание пакета.  
  
> [!NOTE]  
>  При проектировании пакета и отладке скрипта код скрипта временно записывается в файл проекта. Хранение конфиденциальных сведений в файле представляет потенциальный риск для безопасности, поэтому в код скрипта не рекомендуется включать конфиденциальные данные, например пароли.  
  
 По умолчанию параметр **Option Strict** в интегрированной среде разработки отключен.  
  
## <a name="script-task-project-structure"></a>Структура проекта задачи «Скрипт»  
 При создании или изменении скрипта, содержащегося в задаче «Скрипт» средства VSTA открывают новый пустой проект или повторно открывают существующий проект. Создание этого проекта VSTA не влияет на развертывание пакета, поскольку проект сохраняется внутри пакетного файла и задача «Скрипт» не создает дополнительных файлов.  
  
### <a name="project-items-and-classes-in-the-script-task-project"></a>Элементы и классы проекта в проекте задачи «Скрипт»  
 По умолчанию проект задачи "Скрипт", отображаемый в окне обозревателя проектов VSTA, содержит один элемент — **ScriptMain**. В свою очередь, элемент **ScriptMain** содержит один класс, именуемый **ScriptMain**. Элементы кода в классе изменяются в зависимости от языка программирования, выбранного для задачи «Скрипт».  
  
-   Если задача "Скрипт" настроена для языка программирования [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)], класс **ScriptMain** содержит открытую подпрограмму **Main**. Подпрограмма **ScriptMain.Main** является методом, который вызывается во время выполнения задачи "Скрипт".  
  
     По умолчанию единственным кодом в подпрограмме **Main** нового скрипта является строка `Dts.TaskResult = ScriptResults.Success`. Эта строка извещает среду выполнения об успешной работе задачи. Свойство **Dts.TaskResult** описано в разделе [Возврат результатов из задачи "Скрипт"](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md).  
  
-   Если для задачи "Скрипт" задан язык программирования Visual C#, то класс **ScriptMain** имеет публичный метод **Main**. Этот метод вызывается при запуске задачи «Скрипт».  
  
     По умолчанию метод **Main** включает строку `Dts.TaskResult = (int)ScriptResults.Success`. Эта строка извещает среду выполнения об успешной работе задачи.  
  
 Элемент **ScriptMain** может содержать классы, отличные от класса **ScriptMain**. Классы доступны только задаче «Скрипт», в которой они находятся.  
  
 По умолчанию элемент проекта **ScriptMain** содержит следующий автоматически формируемый код. В шаблоне кода также имеются общие сведения о задаче «Скрипт» и дополнительные сведения о получении и управлении такими объектами служб SSIS, как переменные, события и подключения.  
  
```vb  
' Microsoft SQL Server Integration Services Script Task  
' Write scripts using Microsoft Visual Basic 2008.  
' The ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy  
  
<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _  
Partial Class ScriptMain  
  
Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup  
  
End Sub  
  
Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown  
Try  
' Unlock variables from the read-only and read-write variable collection properties  
If (Dts.Variables.Count <> 0) Then  
Dts.Variables.Unlock()  
End If  
Catch ex As Exception  
        End Try  
End Sub  
  
Enum ScriptResults  
Success = DTSExecResult.Success  
Failure = DTSExecResult.Failure  
End Enum  
  
' The execution engine calls this method when the task executes.  
' To access the object model, use the Dts property. Connections, variables, events,  
' and logging features are available as members of the Dts property as shown in the following examples.  
'  
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value  
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)  
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)  
'  
' To use the connections collection use something like the following:  
' ConnectionManager cm = Dts.Connections.Add("OLEDB")  
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"  
'  
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
'   
' To open Help, press F1.  
  
Public Sub Main()  
'  
' Add your code here  
'  
Dts.TaskResult = ScriptResults.Success  
End Sub  
  
End Class  
```  
  
```csharp  
/*  
   Microsoft SQL Server Integration Services Script Task  
   Write scripts using Microsoft Visual C# 2008.  
   The ScriptMain is the entry point class of the script.  
*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;  
using System.Windows.Forms;  
  
namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj  
{  
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]  
    public partial class ScriptMain  
    {  
        private void ScriptMain_Startup(object sender, EventArgs e)  
        {  
  
        }  
  
        private void ScriptMain_Shutdown(object sender, EventArgs e)  
        {  
            try  
            {  
                // Unlock variables from the read-only and read-write variable collection properties  
                if (Dts.Variables.Count != 0)  
                {  
                    Dts.Variables.Unlock();  
                }  
            }  
            catch  
            {  
            }  
        }  
  
        #region VSTA generated code  
        private void InternalStartup()  
        {  
            this.Startup += new System.EventHandler(ScriptMain_Startup);  
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);  
        }  
        enum ScriptResults  
        {  
            Success = DTSExecResult.Success,  
            Failure = DTSExecResult.Failure  
        };  
  
        #endregion  
  
        /*  
The execution engine calls this method when the task executes.  
To access the object model, use the Dts property. Connections, variables, events,  
and logging features are available as members of the Dts property as shown in the following examples.  
  
To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;  
To post a log entry, call Dts.Log("This is my log text", 999, null);  
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);  
  
To use the connections collection use something like the following:  
ConnectionManager cm = Dts.Connections.Add("OLEDB");  
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";  
  
Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
  
To open Help, press F1.  
*/  
  
        public void Main()  
        {  
            // TODO: Add your code here  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
    }  
```  
  
### <a name="additional-project-items-in-the-script-task-project"></a>Дополнительные элементы проекта в проекте задачи «Скрипт»  
 Проект задачи "Скрипт" может содержать элементы, отличные от элемента **ScriptMain** по умолчанию. К проекту можно добавлять классы, модули и файлы кодов. Можно также использовать папки для организации групп элементов. Все добавляемые элементы сохраняются внутри пакета.  
  
### <a name="references-in-the-script-task-project"></a>Ссылки в проекте задачи «Скрипт»  
 Чтобы добавить ссылки в управляемые сборки, щелкните правой кнопкой мыши проект задачи "Скрипт" в **Обозревателе проектов**, затем выберите **Добавить ссылку**. Дополнительные сведения см. в разделе [Ссылки на другие сборки в решениях со сценариями](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  Ссылки проекта можно просмотреть в среде разработки VSTA в **представлении классов** или в **обозревателе проектов**. Любое из этих окон можно открыть из меню **Вид**. Можно добавить новую ссылку из меню **Проект**, из **обозревателя проектов** или из **представления классов**.  
  
## <a name="interacting-with-the-package-in-the-script-task"></a>Взаимодействие с пакетом в задаче «Скрипт»  
 Задача "Скрипт" использует глобальный объект **Dts**, являющийся экземпляром класса <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>, а его элементы должны взаимодействовать с содержащим их пакетом и со средой выполнения служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 В следующей таблице представлены основные открытые элементы класса <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>, который представлен в коде задачи "Скрипт" через глобальный объект **Dts**. В этом разделе более подробно рассматривается использование этих элементов.  
  
|Член|Назначение|  
|------------|-------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|Предоставляет доступ к диспетчерам соединений, определенным в пакете.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|Предоставляет интерфейс событий, чтобы задача «Скрипт» могла инициировать ошибки, предупреждения и информационные сообщения.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|Предоставляет простой способ возвращения одного объекта в среду выполнения (в дополнение к **TaskResult**), который может также использоваться для ветвления рабочего процесса.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|Записывает во включенные регистраторы данные, такие как ход выполнения задачи и результаты.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|Сообщает об успешном или неуспешном выполнении задачи.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|Предоставляет транзакцию, если она имеется, в которой работает контейнер задачи.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|Предоставляет доступ к используемым в скрипте переменным, указанным в свойствах **ReadOnlyVariables** и **ReadWriteVariables** задачи.|  
  
 Класс <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> содержит также некоторые открытые элементы, которые, вероятно, не будут использованы.  
  
|Член|Описание|  
|------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|Свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> предоставляет более удобный доступ к переменным. Хотя можно использовать <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, необходимо явно вызывать методы для блокировки и разблокировки переменных для чтения и записи. Задача «Скрипт» прозрачно обрабатывает семантику блокировки при использовании свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.|  
  
## <a name="debugging-the-script-task"></a>Отладка задачи «Скрипт»  
 Для отладки кода в задаче «Скрипт» установите в коде по крайней мере одну точку останова, а затем закройте среду разработки VSTA IDE, чтобы запустить пакет в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Когда выполнение пакета входит в задачу «Скрипт», среда разработки VSTA IDE открывается повторно и отображает код в режиме только для чтения. После того как выполнение достигает точку останова, можно проверить значения переменных и выполнить оставшийся код в режиме пошагового выполнения.  
  
> [!WARNING]  
>  При выполнении пакета в 64-разрядном режиме задачу "Сценарий" невозможно отлаживать.  
  
> [!NOTE]  
>  Для отладки задачи «Скрипт» необходимо выполнить пакет. Если выполняется только отдельная задача, точки останова в коде задачи «Скрипт» пропускаются.  
  
> [!NOTE]  
>  Однако нельзя выполнять отладку задачи «Скрипт», если задача запускается как часть дочернего пакета, вызываемого задачей «Выполнение пакета». В этом случае точки останова, установленные в задаче «Скрипт» в дочернем пакете, пропускаются. Дочерний пакет можно нормально отладить, запустив его отдельно.  
  
> [!NOTE]  
>  Во время отладки пакета, содержащего несколько задач «Скрипт», отладчик выполняет отладку одной задачи «Скрипт». Затем система может выполнять отладку другой задачи «Скрипт», если отладчик завершает работу, как в случае контейнера «цикл по элементам» или «цикл по каждому элементу».  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [Затруднения при установке и настройке VSTA для установок SSIS 2008 и R2](https://go.microsoft.com/fwlink/?LinkId=215661) на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Ссылки на другие сборки в решениях со скриптами](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)   
 [Настройка задачи «Скрипт» в редакторе задачи «Скрипт»](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
  
  
