---
title: Создание атрибута даты (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
caps.latest.revision: 13
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ed22116162d011deddd11ae8b019de10b96b12f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-date-attribute-master-data-services"></a>Создание атрибута даты (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибут даты создается, если нужно, чтобы пользователи вводили даты как значения атрибута.  
  
> [!NOTE]  
>  Атрибут называется DateTime, но значения времени не поддерживаются.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Должна существовать сущность, для которой создается атрибут. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-date-attribute"></a>Создание атрибута даты  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий, а затем нажмите кнопку **Добавить**.  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Введите имя атрибута в поле **Имя** . Список слов, которые не должны использоваться как имена атрибутов, см. в разделе [Зарезервированные слова (службы Master Data Services)](../master-data-services/reserved-words-master-data-services.md).  
  
7.  При необходимости введите отображаемое имя и **Описание** атрибута.  
  
8.  В поле **Ширина отображаемой области (в пикселях)** введите ширину столбца атрибута для отображения в сетке **обозревателя** .  
  
9. В списке **Тип атрибута** выберите **Свободная форма**.  
  
10. В списке **Тип данных** выберите **DateTime**.  
  
11. Выберите из списка **Маска ввода** формат дат.  
  
12. По желанию установите флажок **Включить отслеживание изменений** , чтобы отслеживать изменения в группах атрибутов. Дополнительные сведения см. в разделе [Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Нажмите кнопку **Сохранить**.  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a>Отображение части времени значения типа datetime  
 Чтобы пользовательский интерфейс отображал время из значения типа datetime, необходимо выбрать подходящую маску ввода для этого атрибута. Для этого не подходит ни одна из встроенных масок для атрибутов значения типа Datetime, но вы можете добавить новую маску, которая позволит отобразить значение времени. Для этого добавьте строку в таблицу mdm.tblList базы данных MDS, где будут храниться встроенные маски. Строка должна иметь следующие значения:  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Маска ввода|  
|Seq|19|  
|List Option|dd/MM/yyyy hh:mm:ss tt|  
|Option ID|19|  
|IsVisible|1|  
|Group_ID|3|  
  
 После ввода строки с приведенными выше значениями в таблицу mdm.tblList маска dd/MM/yyyy hh:mm:ss tt становится доступной в списке масок ввода. Теперь вы можете выбрать эту маску для отображения даты и времени в столбце атрибутов datetime сущности в обозревателе MDS.  
  
 Маска ввода — это настраиваемая строка форматирования даты и времени .NET. Дополнительную информацию см. в разделе [Настраиваемые строки формата даты и времени](https://msdn.microsoft.com/en-us/library/8kb3ddd4\(v=vs.110\).aspx)  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)   
 [Изменение имени атрибута и типа данных (службы Master Data Services)](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Создание файлового атрибута (службы Master Data Services)](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
