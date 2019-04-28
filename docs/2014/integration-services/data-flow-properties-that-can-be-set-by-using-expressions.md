---
title: Поток данных, которые могут устанавливаться с помощью выражений свойств | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fbb609a65c70cb44c8fda81feb75927060ed289b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829146"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a>Свойства потока данных, которые можно задавать с помощью выражений
  Значения определенных свойств объектов потока данных можно указать с помощью выражений свойств, доступных в контейнере задачи потока данных.  
  
 Дополнительные сведения о выражениях свойств см. в разделе [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md).  
  
 Выражения свойств можно использовать для настройки конфигурации каждого развернутого экземпляра пакета. Выражения свойств также можно использовать, чтобы задать ограничения времени выполнения пакета с помощью параметра **/set** программы командной строки **dtexec** . Например, можно ограничить значение `MaximumThreads` для преобразования «Сортировка» или значение `MaxMemoryUsage` для преобразований «Нечеткое группирование» и «Нечеткий уточняющий запрос». При отсутствии ограничений эти преобразования могут кэшировать большие объемы данных в памяти.  
  
 Чтобы задать выражение свойств для одного из свойств объектов потока данных, перечисленных в этом разделе, откройте окно **Свойства** для задачи потока данных, выбрав задачу потока данных в области конструктора **Поток управления** или перейдя в конструкторе на вкладку **Поток данных** , не указывая отдельных компонентов или пути. Выберите свойство **Выражения** и нажмите кнопку с многоточием (...), чтобы отобразить диалоговое окно **Редактор выражений свойств** . Выберите свойство из раскрывающегося списка **Свойство** , затем введите выражение в текстовом поле **Выражение** и нажмите кнопку с многоточием (...), чтобы отобразить диалоговое окно **Построитель выражений** .  
  
 Список **Свойство** содержит доступные свойства только для объектов потока данных, уже помещенных в область **Поток данных** конструктора. Поэтому нельзя использовать список **Свойство** для просмотра всех возможных свойств объектов потока данных, которые поддерживают выражения свойств. Например, если источник ADO NET помещен в рабочей области конструктора **свойство** список содержит запись для `[ADO NET Source].[SqlCommand]` свойство. Список также отображает многие свойства самой задачи потока данных.  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a>Свойства объектов потока данных, которые поддерживают выражения свойств  
 Значения свойств в следующем списке могут быть заданы с использованием выражений свойств.  
  
### <a name="data-flow-sources"></a>Источники потока данных  
  
|Объект потока данных|Свойство|  
|----------------------|--------------|  
|источник ADO NET|Свойство TableOrViewName<br /><br /> Свойство SqlCommand|  
|XML-источник|Свойство XMLData<br /><br /> Свойство XMLSchemaDefinition|  
  
### <a name="data-flow-transformations"></a>Преобразования потока данных  
 Дополнительные сведения об этих пользовательских свойствах см. в разделе [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
|Объект потока данных|Свойство|  
|----------------------|--------------|  
|преобразование «Условное разбиение»|Свойство FriendlyExpression|  
|преобразование «Производный столбец»|Свойство FriendlyExpression|  
|преобразование «Нечеткое группирование»|Свойство MaxMemoryUsage|  
|преобразование «Нечеткий уточняющий запрос»|Свойство MaxMemoryUsage|  
|Преобразование «Уточняющий запрос»|Свойство SqlCommand<br /><br /> Свойство SqlCommandParam|  
|преобразование «Команда OLE DB»|Свойство SqlCommand|  
|преобразование «Процентная выборка»|Свойство SamplingValue|  
|преобразование «Сведение»|Свойство PivotKeyValue|  
|преобразование «Выборка строк»|Свойство SamplingValue|  
|преобразование «Сортировка»|Свойство MaximumThreads|  
|Преобразование отмены свертывания|Свойство PivotKeyValue|  
  
### <a name="data-flow-destinations"></a>Назначения потока данных  
  
|Объект потока данных|Свойство|  
|----------------------|--------------|  
|Назначение «ADO.NET»|Свойство TableOrViewName<br /><br /> Свойство BatchSize<br /><br /> Свойство CommandTimeout|  
|назначение «Неструктурированный файл»|Свойство Header|  
|Назначение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact|Свойство TableName|  
|Назначение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Свойство BulkInsertTableName<br /><br /> Свойство BulkInsertFirstRow<br /><br /> Свойство BulkInsertLastRow<br /><br /> Свойство BulkInsertOrder<br /><br /> Свойство Timeout|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Добавление или изменение выражение свойства](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)на сайте pragmaticworks.com  
  
## <a name="see-also"></a>См. также  
 [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md)   
 [Common Properties](../../2014/integration-services/common-properties.md)   
 [Пользовательские свойства преобразования](data-flow/transformations/transformation-custom-properties.md)   
 [Свойства пути](../../2014/integration-services/path-properties.md)  
  
  
