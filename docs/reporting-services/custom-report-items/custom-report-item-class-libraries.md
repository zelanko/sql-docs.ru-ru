---
title: "Библиотеки классов пользовательского отчета элемент | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
caps.latest.revision: 27
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f216228c01e835e88cd9d4c7d7d4190648a386db
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="custom-report-item-class-libraries"></a>Библиотеки классов пользовательского элемента отчета
  Пользовательские элементы отчета использовать классы из **Microsoft.ReportDesigner** пространства имен. Классы, используемые для реализации пользовательского элемента отчета, можно разделить на две основные группы: уникальные классы, созданные для поддержки инфраструктуры пользовательских элементов отчетов, и управляемые классы-оболочки, инкапсулирующие функциональные возможности соответствующих элементов языка определения отчетов. Пример кода по использованию этих классов см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-infrastructure-classes"></a>Классы инфраструктуры пользовательского элемента отчета  
 Для реализации пользовательского элемента отчета используются следующие классы.  
  
> [!NOTE]  
>  Приводимые далее в таблицах списки неполны; в них перечислены только наиболее часто используемые методы и свойства для каждого класса.  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a>Microsoft.ReportDesigner.CustomReportItemDesigner  
 Это главный класс пользовательского элемента отчета. Главный класс реализации пользовательского элемента отчета должен быть производным от этого класса.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|**Название**|Имя пользовательского элемента отчета.|  
|**Тип**|Тип пользовательского элемента отчета.|  
|**CustomData**|Объект <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>, инкапсулирующий свойства данных пользовательского элемента отчета, заданные во время разработки.|  
|**Настраиваемые свойства**|Коллекция пользовательских свойств пользовательского элемента отчета.|  
|**Высота**|Высота элемента управления пользовательского элемента отчета.|  
|**Ширина**|Ширина элемента управления пользовательского элемента отчета.|  
|**Отчет**|Контейнер для свойств уровня отчета, таких как список наборов данных отчета.|  
|**AltReportItem**|Альтернативный объект — элемент отчета, который будет использоваться там, где не поддерживается элемент управления времени выполнения для пользовательского элемента отчета.|  
|**Style**|Свойства стиля для пользовательского элемента отчета.|  
|**Крайний элемент**|Окно дополнения, используемое для интерактивного редактирования элемента управления.|  
|**Сайт**|**ISite** компонента.|  
|**DesignerVerbCollection**|Набор пользовательских команд, доступных через контекстное меню элемента управления.|  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**BeginEdit**|Активизирует интерактивное редактирование элемента управления.|  
|**DoDefaultAction**|Вызывается двойным щелчком или нажатием клавиши ВВОД в элементе управления.|  
|**EndEdit**|Деактивирует интерактивное редактирование элемента управления.|  
|**GetService**|Возвращает объект, представляющий собой службу.|  
|**InitializeNewComponent**|Вызывается при создании нового пользовательского элемента отчета.|  
|**Сделать недействительным**|Перерисовывает всю область элемента управления.|  
|**OnDragEnter**<br /><br /> **OnDragDrop**|Вызывается при перетаскивании объекта на элемент управления.|  
|**OnPaint**|Вызывается в ответ на **Paint** событий.|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a>Microsoft.ReportDesigner.CustomReportItemAttribute  
 Атрибут используется для выяснения типа пользовательского элемента отчета. Имя должно соответствовать значение \< **имя**> атрибут **ReportItem** элемент в файле конфигурации конструктора отчетов.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**CustomReportItemAttribute**|Создает объект CustomReportItemAttribute.|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a>Microsoft.ReportDesigner.LocalizedNameAttribute  
 Этот атрибут позволяет указать отображаемое имя, предназначенное для конструктора пользовательского элемента отчета.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**LocalizedNameAttribute**|Создает объект LocalizedNameAttribute.|  
  
### <a name="microsoftreportdesigneradornment"></a>Microsoft.ReportDesigner.Adornment  
 **Оформления** класс используется компонента пользовательского элемента отчета времени разработки для предоставления областей за пределами основного прямоугольника области конструктора. Эти области могут обрабатывать события пользовательского интерфейса, такие как щелчки кнопкой мыши и операции перетаскивания.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**OnShow**|Вызывается, когда **оформления** активируется.|  
|**OnHide**|Вызывается, когда **оформления** отключена.|  
|**Paint**|Вызывается в ответ на **Paint** событий.|  
|**OnDragEnter**<br /><br /> **OnDragOver**<br /><br /> **OnDragLeave**<br /><br /> **OnDragDrop**|Вызывается, когда объект перетаскивается в **оформления**.|  
  
### <a name="microsoftreportdesigneradornerservice"></a>Microsoft.ReportDesigner.AdornerService  
 Этот класс используется для предоставления коллекции служб отображения, используемые пользовательского элемента отчета для поддержки **оформления** объекты для компонента пользовательского элемента отчета во время разработки.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|**AdornerWindowBounds**|Границы окна Adorner.|  
|**AdornerWindowRegion**|Область окна Adorner.|  
|**AdornerWindowGraphics**|Графический контекст окна Adorner.|  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**ComponentRectInDesignerFrame**|Возвращает границы компонента, преобразованные в координаты экрана конструктора.|  
|**InvalidateAdorner**|Делает недействительным окно Adorner.|  
|**PointToAdorner**|Возвращает точку в экранных координатах, преобразованных в координаты окна Adorner.|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a>Microsoft.ReportDesigner.ExpressionEditor  
 Этот класс можно использовать из элемента управления времени разработки пользовательского элемента отчета для вызова редактора выражений.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|**EditValue**|Вызывает редактор выражений, инициализированный значением данного объекта.|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a>Microsoft.ReportDesigner.IFieldsDataObject  
 Этот класс представляет собой коллекцию полей служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и используется для поддержки событий перетаскивания в среде разработки. Наследует от **IReportItemDataObject**.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|**DataSetName**|Имя набора данных, содержащего поля, которые предназначены для перетаскивания.|  
|**Поля**|Коллекция полей (**Microsoft.ReportDesigner.Field**) для удаления.|  
  
## <a name="see-also"></a>См. также:  
 [Язык определения отчетов &#40; Службы SSRS &#41;](../../reporting-services/reports/report-definition-language-ssrs.md)   
 [Создание компонента пользовательского элемента отчета времени выполнения](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента пользовательского элемента отчета времени разработки](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)  
  
  
