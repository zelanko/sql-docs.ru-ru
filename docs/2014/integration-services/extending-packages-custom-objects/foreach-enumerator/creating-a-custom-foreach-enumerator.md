---
title: Создание пользовательского перечислителя по каждому элементу | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d9226cfd55b6851779564baced0c745e8a17686b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968767"
---
# <a name="creating-a-custom-foreach-enumerator"></a>Создание пользовательского перечислителя по каждому элементу
  Создание пользовательского перечислителя по каждому элементу, как и любого другого пользовательского объекта для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], осуществляется за несколько шагов, а именно:  
  
-   Создайте новый класс, наследующий базовый класс. Для перечислителя по каждому элементу базовым классом является <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Для перечислителя по каждому элементу используется атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Наиболее важным методом для перечислителя по каждому элементу является <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>.  
  
-   При необходимости разработайте настраиваемый пользовательский интерфейс. В случае с перечислителем по каждому элементу для этого необходимо использовать класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI>.  
  
 Пользовательский перечислитель размещается в контейнере <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>. Во время выполнения контейнером <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> вызывается метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> пользовательского перечислителя. Пользовательский перечислитель возвращает объект, реализующий интерфейс `IEnumerable`, например, `ArrayList`. Затем перечислитель <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> просматривает последовательно все элементы коллекции, передает значение текущего элемента в поток управления через определяемую пользователем переменную и выполняет поток управления в контейнере.  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a>Приступая к работе над пользовательским перечислителем по каждому элементу  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Так как все управляемые перечислители по каждому элементу являются производными от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, на первом шаге создания пользовательского перечислителя по каждому элементу необходимо создать проект библиотеки классов на предпочитаемом языке программирования управляемого кода, а затем создать класс, наследующий от базового класса. В этом производном классе будут переопределены методы и свойства базового класса, реализующие пользовательские функциональные возможности.  
  
 Создайте в том же решении второй проект библиотеки классов для собственного пользовательского интерфейса. Для пользовательского интерфейса рекомендуется использовать отдельную сборку, что позволяет обновлять и заново развертывать перечислитель по каждому элементу или его пользовательский интерфейс независимо друг от друга.  
  
 Настройте в обоих проектах подписывание сборок, которые будут создаваться во время построения, с помощью файла ключа для строгого имени.  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a>Применение атрибута DtsForEachEnumerator  
 Примените к созданному классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>, чтобы определить его как перечислитель по каждому элементу. Этот атрибут содержит сведения для времени разработки, например, имя и описание перечислителя по каждому элементу. `Name`Свойство отображается в раскрывающемся списке доступных перечислителей на вкладке **коллекция** диалогового окна **Редактор циклов по каждому** элементу.  
  
 Используйте свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A>, чтобы связать перечислитель по каждому элементу с его пользовательским интерфейсом. Чтобы получить токен открытого ключа, необходимый для этого свойства, можно использовать команду **sn.exe -t**, отображающую токен открытого ключа из SNK-файла пары ключей, который предназначен для подписывания сборки пользовательского интерфейса.  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a>Построение, развертывание и отладка пользовательского перечислителя  
 Построение, развертывание и отладка пользовательского перечислителя по каждому элементу в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] осуществляется за несколько шагов, аналогичных используемым при работе с другими типами пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md).  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Написание кода пользовательского перечислителя Foreach](coding-a-custom-foreach-enumerator.md)   
 [Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
