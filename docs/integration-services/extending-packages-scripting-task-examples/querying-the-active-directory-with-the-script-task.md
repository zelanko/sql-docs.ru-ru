---
title: "Запрос Active Directory с помощью задачи «скрипт» | Документы Microsoft"
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
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee5a82829785e78554b105e1f3bf3bd24f05b778
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="querying-the-active-directory-with-the-script-task"></a>Запрос Active Directory в задаче «Скрипт»
  Часто задачей корпоративных приложений обработки данных, например, пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], является обработка данных различным образом, в зависимости от категории, названия должности, иных характеристик сотрудников, сведения о которых хранятся в службе каталогов Active Directory. Active Directory — [!INCLUDE[msCoName](../../includes/msconame-md.md)] службы каталогов Windows, обеспечивающая централизованное хранение метаданных не только о пользователях, но также и о других корпоративных ресурсах, таких как компьютеры и принтеры. **System.DirectoryServices** пространство имен в платформе Microsoft .NET Framework предоставляет классы для работы с Active Directory, которые помогут прямой обработки данных рабочего процесса, в зависимости от типа данных.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 В следующем примере имя сотрудника, название его должности и номер телефона извлекаются из службы каталогов Active Directory в соответствии со значением переменной `email`, которая содержит адрес электронной почты сотрудника. Элементы управления очередностью в пакете могут использовать извлеченные данные, чтобы определить, например, с каким приоритетом – низким или высоким – следует отправить сообщение электронной почты, в зависимости от должности сотрудника.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Создайте три строковые переменные: `email`, `name` и `title`. Введите действительный корпоративный адрес электронной почты в качестве значения переменной `email`.  
  
2.  На **сценарий** страница **редактор задачи «скрипт»**, добавьте `email` переменной **ReadOnlyVariables** свойство.  
  
3.  Добавить `name` и `title` переменных **ReadWriteVariables** свойство.  
  
4.  В проекте скрипта добавьте ссылку на **System.DirectoryServices** пространства имен.  
  
5.  . В коде, используйте **Imports** инструкцию, чтобы импортировать **DirectoryServices** пространства имен.  
  
> [!NOTE]  
>  Для успешного выполнения этого скрипта необходимо, чтобы в сети организации использовалась служба каталогов Active Directory и в ней хранились сведения, используемые в этом примере.  
  
### <a name="code"></a>код  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Техническая статья [обработки данных Active Directory в SSIS](http://go.microsoft.com/fwlink/?LinkId=199588), на сайте social.technet.microsoft.com  
  
  
