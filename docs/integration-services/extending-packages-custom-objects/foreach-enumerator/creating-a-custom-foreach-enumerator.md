---
title: "Создание пользовательского перечислителя по каждому элементу | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords: custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
caps.latest.revision: "53"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e2efdf248c8db4b3e99c808a7e576ee96e83fb7f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="creating-a-custom-foreach-enumerator"></a>Создание пользовательского перечислителя по каждому элементу
  Создание пользовательского перечислителя по каждому элементу, как и любого другого пользовательского объекта для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], осуществляется за несколько шагов, а именно:  
  
-   Создайте новый класс, наследующий базовый класс. Для перечислителя по каждому элементу базовым классом является <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Для перечислителя по каждому элементу используется атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Наиболее важным методом для перечислителя по каждому элементу является <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>.  
  
-   При необходимости разработайте настраиваемый пользовательский интерфейс. В случае с перечислителем по каждому элементу для этого необходимо использовать класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI>.  
  
 Пользовательский перечислитель размещается в контейнере <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>. Во время выполнения контейнером <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> вызывается метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> пользовательского перечислителя. Пользовательский перечислитель возвращает объект, реализующий интерфейс **IEnumerable**, например **ArrayList**. Затем перечислитель <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> просматривает последовательно все элементы коллекции, передает значение текущего элемента в поток управления через определяемую пользователем переменную и выполняет поток управления в контейнере.  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a>Приступая к работе над пользовательским перечислителем по каждому элементу  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Так как все управляемые перечислители по каждому элементу являются производными от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, на первом шаге создания пользовательского перечислителя по каждому элементу необходимо создать проект библиотеки классов на предпочитаемом языке программирования управляемого кода, а затем создать класс, наследующий от базового класса. В этом производном классе будут переопределены методы и свойства базового класса, реализующие пользовательские функциональные возможности.  
  
 Создайте в том же решении второй проект библиотеки классов для собственного пользовательского интерфейса. Для пользовательского интерфейса рекомендуется использовать отдельную сборку, что позволяет обновлять и заново развертывать перечислитель по каждому элементу или его пользовательский интерфейс независимо друг от друга.  
  
 Настройте в обоих проектах подписывание сборок, которые будут создаваться во время построения, с помощью файла ключа для строгого имени.  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a>Применение атрибута DtsForEachEnumerator  
 Примените к созданному классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>, чтобы определить его как перечислитель по каждому элементу. Этот атрибут содержит сведения для времени разработки, например, имя и описание перечислителя по каждому элементу. Свойство **Name** отображается в раскрывающемся списке доступных перечислителей на вкладке **Коллекция** диалогового окна **Редактор циклов по каждому элементу**.  
  
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
 Построение, развертывание и отладка пользовательского перечислителя по каждому элементу в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] осуществляется за несколько шагов, аналогичных используемым при работе с другими типами пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="see-also"></a>См. также:  
 [Написание кода пользовательского перечислителя по каждому элементу](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)   
 [Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
