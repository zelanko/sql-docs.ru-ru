---
title: Создание пользовательского диспетчера подключений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c285b74765fea81374c8cfbb861851c35323fd68
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271776"
---
# <a name="creating-a-custom-connection-manager"></a>Создание пользовательского диспетчера соединений
  Создание пользовательского диспетчера соединений осуществляется за несколько шагов, аналогично созданию любого другого пользовательского объекта служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Создайте новый класс, наследующий базовый класс. Для диспетчера соединений базовым классом является <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Для диспетчера соединений используется атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Для диспетчера соединений это свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A>, методы <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>.  
  
-   При необходимости разработайте настраиваемый пользовательский интерфейс. В случае с диспетчером соединений для этого необходимо использовать класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>.  
  
> [!NOTE]  
>  Большая часть задач, источников и назначений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] работает только с определенными типами встроенных диспетчеров соединений. Поэтому данные образцы нельзя протестировать с помощью встроенных задач и компонентов.  
  
## <a name="getting-started-with-a-custom-connection-manager"></a>Приступая к работе над пользовательским диспетчером соединений  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Так как все управляемые диспетчеры соединений являются производными от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, на первом шаге создания пользовательского диспетчера соединений необходимо создать проект библиотеки классов на предпочитаемом языке программирования управляемого кода, а затем создать класс, наследующий от базового класса. В этом производном классе будут переопределены методы и свойства базового класса, чтобы реализовать пользовательские функциональные возможности.  
  
 Создайте в том же решении второй проект библиотеки классов для собственного пользовательского интерфейса. Для пользовательского интерфейса рекомендуется использовать отдельную сборку, что позволяет обновлять и заново развертывать диспетчер соединений или его пользовательский интерфейс независимо друг от друга.  
  
 Настройте в обоих проектах подписывание сборок, которые будут создаваться во время построения, с помощью файла ключа для строгого имени.  
  
### <a name="applying-the-dtsconnection-attribute"></a>Применение атрибута DtsConnection  
 Примените к созданному классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>, чтобы определить его в качестве диспетчера соединений. Этот атрибут содержит сведения для времени разработки, например, имя, описание и тип соединения диспетчера соединений. Свойства <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> и **Description** соответствуют столбцам **Тип** и **Описание** в диалоговом окне **Добавление диспетчера соединений со службами SSIS**, которое отображается при настройке соединений пакета в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 Используйте свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A>, чтобы связать диспетчер соединений с его пользовательским интерфейсом. Чтобы получить токен открытого ключа, необходимый для этого свойства, можно использовать команду **sn.exe -t**, отображающую токен открытого ключа из SNK-файла пары ключей, который предназначен для подписывания сборки пользовательского интерфейса.  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a>Построение, развертывание и отладка пользовательского диспетчера соединений  
 Построение, развертывание и отладка пользовательского диспетчера соединений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] осуществляется в несколько шагов, аналогичных используемым при работе с другими типами пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).    
  
## <a name="see-also"></a>См. также:  
 [Написание кода пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/coding-a-custom-connection-manager.md)   
 [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
