---
title: Создание пользовательской задачи | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06ff2d20ee28c67fa95db4f4ef5f8f1f65862e04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227765"
---
# <a name="creating-a-custom-task"></a>Создание пользовательской задачи
  Шаги, необходимые для создания пользовательской задачи, аналогичны шагам, необходимым для создания любого другого пользовательского объекта служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
-   Создайте новый класс, наследующий базовый класс. Базовым классом для задачи является класс <xref:Microsoft.SqlServer.Dts.Runtime.Task>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Атрибутом для задачи является атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Для задачи это методы <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
-   При необходимости разработайте настраиваемый пользовательский интерфейс. Для задачи необходим класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>.  
  
## <a name="getting-started-with-a-custom-task"></a>Приступая к работе с пользовательской задачей  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Поскольку все управляемые задачи являются наследниками базового класса <xref:Microsoft.SqlServer.Dts.Runtime.Task>, первым шагом при создании пользовательской задачи является создание проекта библиотеки классов и класса, порожденного от этого базового класса, на управляемом языке программирования по выбору. В этом производном классе будут переопределены методы и свойства базового класса, реализующие пользовательские функциональные возможности.  
  
 Создайте в том же решении второй проект библиотеки классов для собственного пользовательского интерфейса. Для простоты развертывания рекомендуется создать для пользовательского интерфейса отдельную сборку, поскольку это позволит обновлять и повторно развертывать диспетчер соединений и пользовательский интерфейс независимо друг от друга.  
  
 Настройте в обоих проектах подписывание сборок, которые будут создаваться во время построения, с помощью файла ключа для строгого имени.  
  
### <a name="applying-the-dtstask-attribute"></a>Применение атрибута DtsTask  
 Примените атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> к созданному классу для идентификации его в качестве задачи. Этот атрибут предоставляет информацию времени разработки, такую как имя, описание и тип задачи.  
  
 Используйте свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> для связывания задачи с пользовательским интерфейсом. Чтобы получить токен открытого ключа, необходимый для этого свойства, можно использовать команду **sn.exe -t**, отображающую токен открытого ключа из SNK-файла пары ключей, который предназначен для подписывания сборки пользовательского интерфейса.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a>Построение, развертывание и отладка пользовательской задачи  
 Шаги по построению, развертыванию и отладке пользовательской задачи в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] аналогичны шагам, необходимым для других типов пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md).  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательской задачи](creating-a-custom-task.md)   
 [Создание кода пользовательской задачи](coding-a-custom-task.md)   
 [Разработка пользовательского интерфейса для пользовательской задачи](developing-a-user-interface-for-a-custom-task.md)  
  
  
