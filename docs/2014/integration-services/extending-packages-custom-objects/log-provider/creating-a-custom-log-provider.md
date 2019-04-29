---
title: Создание пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: db5ec327ab7f7672a55fbaa0d2cd086bbcfc67cd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896306"
---
# <a name="creating-a-custom-log-provider"></a>Создание пользовательского регистратора
  Среда времени выполнения служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] располагает обширными возможностями по ведению журналов. С помощью журнала можно отслеживать события, происходящие во время выполнения пакета. Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] включают целый ряд регистраторов, используя которые можно создавать и сохранять журналы в различных форматах, например в XML, текстовом файле, базе данных или в журнале событий Windows. Если ни один из этих регистраторов или предлагаемых ими выходных форматов не соответствует потребностям пользователя, можно создать пользовательский регистратор.  
  
 Создание пользовательского регистратора, как и любого другого пользовательского объекта для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], осуществляется в несколько шагов, а именно:  
  
-   Создайте новый класс, наследующий базовый класс. Для регистратора базовым классом является <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Для регистратора используется атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Для регистратора это свойство <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>, методы <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.  
  
-   Настраиваемые пользовательские интерфейсы для пользовательских регистраторов в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] не реализуются.  
  
## <a name="getting-started-with-a-custom-log-provider"></a>Приступая к работе над пользовательским регистратором  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Так как все управляемые регистраторы являются производными от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, на первом шаге создания пользовательского регистратора необходимо создать проект библиотеки классов на предпочитаемом языке программирования управляемого кода, а затем создать класс, наследующий от базового класса. В этом производном классе будут переопределены методы и свойства базового класса, реализующие пользовательские функциональные возможности.  
  
 Настройте проект таким образом, чтобы создаваемая сборка подписывалась с использованием файла ключа для строгого имени.  
  
> [!NOTE]  
>  Многие регистраторы служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеют собственный пользовательский интерфейс, в котором реализован интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>, а вместо содержимого текстового поля **Конфигурация** в диалоговом окне **Настройка журналов служб SSIS** используется фильтруемый раскрывающийся список доступных диспетчеров соединений. Однако пользовательские интерфейсы для пользовательских регистраторов не реализуются в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
### <a name="applying-the-dtslogprovider-attribute"></a>Применение атрибута DtsLogProvider  
 Примените к созданному классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>, чтобы определить его в качестве регистратора. Этот атрибут содержит сведения для времени разработки, например, имя и описание регистратора. `DisplayName` И `Description` свойства атрибута соответствуют **имя** и `Description` столбцов, отображаемых в **Настройка журналов служб SSIS** редактором — отображается, когда Настройка ведения журнала для пакета в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
> [!IMPORTANT]  
>  Свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> атрибута не используется. Однако необходимо ввести значение для него, в противном случае пользовательский регистратор не будет отображаться в списке доступных регистраторов.  
  
> [!NOTE]  
>  Поскольку пользовательские интерфейсы для пользовательских регистраторов не реализуются в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], указание значения для свойства <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> не имеет никакого эффекта.  
  
```vb  
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _  
Public Class MyLogProvider  
     Inherits LogProviderBase  
    ' TODO: Override the base class methods.  
End Class  
```  
  
```csharp  
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]  
public class MyLogProvider : LogProviderBase  
{  
    // TODO: Override the base class methods.  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>Построение, развертывание и отладка пользовательского регистратора  
 Построение, развертывание и отладка пользовательского регистратора в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] осуществляется за несколько шагов, аналогичных используемым при работе с другими типами пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md).  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание кода пользовательского регистратора](coding-a-custom-log-provider.md)   
 [Разработка пользовательского интерфейса для пользовательского регистратора](developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
