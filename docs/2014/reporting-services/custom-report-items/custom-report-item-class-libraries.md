---
title: Библиотеки классов пользовательского элемента отчета | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7fc20f857f42c854fcf01947c39ea88206bb5b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63264891"
---
# <a name="custom-report-item-class-libraries"></a>Библиотеки классов пользовательского элемента отчета
  В пользовательских элементах отчетов используются классы из пространства имен `Microsoft.ReportDesigner`. Классы, используемые для реализации пользовательского элемента отчета, можно разделить на две основные группы: уникальные классы, созданные для поддержки инфраструктуры пользовательских элементов отчетов, и управляемые классы-оболочки, инкапсулирующие функциональные возможности соответствующих элементов языка определения отчетов. Образец кода для использования этих классов см. на странице [Образцы продуктов служб SQL Server Reporting](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-infrastructure-classes"></a>Классы инфраструктуры пользовательского элемента отчета  
 Для реализации пользовательского элемента отчета используются следующие классы.  
  
> [!NOTE]  
>  Приводимые далее в таблицах списки неполны; в них перечислены только наиболее часто используемые методы и свойства для каждого класса.  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a>Microsoft.ReportDesigner.CustomReportItemDesigner  
 Это главный класс пользовательского элемента отчета. Главный класс реализации пользовательского элемента отчета должен быть производным от этого класса.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|`Name`|Имя пользовательского элемента отчета.|  
|`Type`|Тип пользовательского элемента отчета.|  
|`CustomData`|Объект <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>, инкапсулирующий свойства данных пользовательского элемента отчета, заданные во время разработки.|  
|`CustomProperties`|Коллекция пользовательских свойств пользовательского элемента отчета.|  
|`Height`|Высота элемента управления пользовательского элемента отчета.|  
|`Width`|Ширина элемента управления пользовательского элемента отчета.|  
|`Report`|Контейнер для свойств уровня отчета, таких как список наборов данных отчета.|  
|`AltReportItem`|Альтернативный объект — элемент отчета, который будет использоваться там, где не поддерживается элемент управления времени выполнения для пользовательского элемента отчета.|  
|`Style`|Свойства стиля для пользовательского элемента отчета.|  
|`Adornment`|Окно дополнения, используемое для интерактивного редактирования элемента управления.|  
|`Site`|`ISite` компонента.|  
|`DesignerVerbCollection`|Набор пользовательских команд, доступных через контекстное меню элемента управления.|  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`BeginEdit`|Активизирует интерактивное редактирование элемента управления.|  
|`DoDefaultAction`|Вызывается двойным щелчком или нажатием клавиши ВВОД в элементе управления.|  
|`EndEdit`|Деактивирует интерактивное редактирование элемента управления.|  
|`GetService`|Возвращает объект, представляющий собой службу.|  
|`InitializeNewComponent`|Вызывается при создании нового пользовательского элемента отчета.|  
|`Invalidate`|Перерисовывает всю область элемента управления.|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|Вызывается при перетаскивании объекта на элемент управления.|  
|`OnPaint`|Вызывается в ответ на событие `Paint`.|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a>Microsoft.ReportDesigner.CustomReportItemAttribute  
 Атрибут используется для выяснения типа пользовательского элемента отчета. Имя должно соответствовать значение <`Name`> атрибут `ReportItem` элемент в файле конфигурации конструктора отчетов.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|Создает объект CustomReportItemAttribute.|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a>Microsoft.ReportDesigner.LocalizedNameAttribute  
 Этот атрибут позволяет указать отображаемое имя, предназначенное для конструктора пользовательского элемента отчета.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|Создает объект LocalizedNameAttribute.|  
  
### <a name="microsoftreportdesigneradornment"></a>Microsoft.ReportDesigner.Adornment  
 Класс `Adornment` используется компонентом времени разработки пользовательского элемента отчета для предоставления областей за пределами основного прямоугольника области конструктора. Эти области могут обрабатывать события пользовательского интерфейса, такие как щелчки кнопкой мыши и операции перетаскивания.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`OnShow`|Вызывается при активации объекта `Adornment`.|  
|`OnHide`|Вызывается при деактивации объекта `Adornment`.|  
|`Paint`|Вызывается в ответ на событие `Paint`.|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|Вызывается при перетаскивании объекта на элемент управления `Adornment`.|  
  
### <a name="microsoftreportdesigneradornerservice"></a>Microsoft.ReportDesigner.AdornerService  
 Этот класс используется для предоставления коллекции служб отображения, используемых пользовательским элементом отчета для поддержки объектов `Adornment` для компонента времени разработки пользовательского элемента отчета.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|`AdornerWindowBounds`|Границы окна Adorner.|  
|`AdornerWindowRegion`|Область окна Adorner.|  
|`AdornerWindowGraphics`|Графический контекст окна Adorner.|  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|Возвращает границы компонента, преобразованные в координаты экрана конструктора.|  
|`InvalidateAdorner`|Делает недействительным окно Adorner.|  
|`PointToAdorner`|Возвращает точку в экранных координатах, преобразованных в координаты окна Adorner.|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a>Microsoft.ReportDesigner.ExpressionEditor  
 Этот класс можно использовать из элемента управления времени разработки пользовательского элемента отчета для вызова редактора выражений.  
  
#### <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|`EditValue`|Вызывает редактор выражений, инициализированный значением данного объекта.|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a>Microsoft.ReportDesigner.IFieldsDataObject  
 Этот класс представляет собой коллекцию полей служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и используется для поддержки событий перетаскивания в среде разработки. Наследует от `IReportItemDataObject`.  
  
#### <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|`DataSetName`|Имя набора данных, содержащего поля, которые предназначены для перетаскивания.|  
|`Fields`|Коллекция полей (`Microsoft.ReportDesigner.Field`), которые предназначены для перетаскивания.|  
  
## <a name="see-also"></a>См. также  
 [Язык определения отчетов (службы SSRS)](../reports/report-definition-language-ssrs.md)   
 [Создание компонента времени выполнения пользовательского элемента отчета](creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента времени разработки пользовательского элемента отчета](creating-a-custom-report-item-design-time-component.md)  
  
  
