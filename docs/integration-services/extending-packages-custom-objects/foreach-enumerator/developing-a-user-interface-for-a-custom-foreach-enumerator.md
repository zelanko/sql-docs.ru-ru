---
title: "Разработка пользовательского интерфейса для пользовательского перечислитель | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e743464fcf482ea51f0cde78d692b367c2be525b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу
  После переопределения реализации свойств и методов базового класса для выполнения пользовательских функций может понадобиться создать настраиваемый пользовательский интерфейс для пользовательского перечислителя по каждому элементу. Если нестандартный пользовательский интерфейс не создается, пользователи могут настраивать новые пользовательские перечислители по каждому элементу только с помощью окна «Свойства».  
  
 В проекте или сборке собственного пользовательского интерфейса создается класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Этот класс является производным от System.Windows.Forms.UserControl, который обычно используется для создания составного элемента управления для размещения других элементов управления Windows Forms. Отображается элемент управления, созданный в **Конфигурация перечислителя** область **коллекции** вкладке **Редактор циклов по каждому элементу**.  
  
> [!IMPORTANT]  
>  После подписи и построения настраиваемого пользовательского интерфейса и его установки в глобальный кэш сборок, как описано в [построение, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md), необходимо указать полное имя этого класса в <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Написание кода для класса элемента управления пользовательского интерфейса  
  
### <a name="initializing-the-user-interface"></a>Инициализация пользовательского интерфейса  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> переопределяется для кэширования ссылок на базовый объект, а также коллекции диспетчеров соединения и переменные, определенные в пакете.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Установка свойств элемента управления пользовательского интерфейса  
 UserControl-класс, из которого создается класс пользовательского интерфейса, предназначен для использования в качестве составного элемента управления для размещения других элементов управления Windows Forms. Поскольку этот класс размещает другие элементы управления, собственный пользовательский интерфейс можно создавать, перетаскивая и упорядочивая элементы управления, устанавливая их свойства и реагируя во время выполнения на формируемые ими события, как в любом другом приложении Windows Forms.  
  
### <a name="saving-settings"></a>Сохранение настроек  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> переопределяется для копирования выбранных пользователем значений при закрытии редактора — от элементов управления до свойств перечислителя.  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательских перечислитель](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Кодирование пользовательский перечислитель](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
  
  

