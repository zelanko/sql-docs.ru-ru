---
title: Запрос Active Directory в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bbcea29ad75eb84b9c8099e5998e307ecbd7943c
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58392072"
---
# <a name="querying-the-active-directory-with-the-script-task"></a>Запрос Active Directory в задаче «Скрипт»
  Часто задачей корпоративных приложений обработки данных, например, пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], является обработка данных различным образом, в зависимости от категории, названия должности, иных характеристик сотрудников, сведения о которых хранятся в службе каталогов Active Directory. Active Directory — служба каталогов [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, обеспечивающая централизованное хранение метаданных не только о пользователях, но и об используемых ими корпоративных ресурсах, например компьютерах и принтерах. Пространство имен `System.DirectoryServices` платформы Microsoft .NET Framework предоставляет классы для работы со службой каталогов Active Directory, с помощью которых можно управлять рабочим процессом по обработке данных в зависимости от типа данных.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Описание  
 В следующем примере имя сотрудника, название его должности и номер телефона извлекаются из службы каталогов Active Directory в соответствии со значением переменной `email`, которая содержит адрес электронной почты сотрудника. Элементы управления очередностью в пакете могут использовать извлеченные данные, чтобы определить, например, с каким приоритетом – низким или высоким – следует отправить сообщение электронной почты, в зависимости от должности сотрудника.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Создайте три строковые переменные: `email`, `name` и `title`. Введите действительный корпоративный адрес электронной почты в качестве значения переменной `email`.  
  
2.  На **сценарий** странице **редактор задачи "скрипт"**, добавьте `email` переменной `ReadOnlyVariables` свойство.  
  
3.  Добавьте переменные `name` и `title` в свойство `ReadWriteVariables`.  
  
4.  В проекте скрипта добавьте ссылку на пространство имен `System.DirectoryServices`.  
  
5.  . Используйте инструкцию `Imports`, чтобы импортировать пространство имен `DirectoryServices`.  
  
> [!NOTE]  
>  Для успешного выполнения этого скрипта необходимо, чтобы в сети организации использовалась служба каталогов Active Directory и в ней хранились сведения, используемые в этом примере.  
  
### <a name="code"></a>Код  
  
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
  
-   Техническая статья [Обработка данных Active Directory в службах SSIS](https://go.microsoft.com/fwlink/?LinkId=199588) на сайте social.technet.microsoft.com  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
