---
title: "Добавить, изменить или удалить значения по умолчанию для параметра отчета | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10460"
- sql13.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: aca61d548532fcb6f61c23130e34bf426c8672c9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-change-or-delete-default-values-for-a-report-parameter"></a>добавить, изменить или удалить значения по умолчанию для параметра отчета
  После создания параметров отчета можно предоставить список значений по умолчанию. Если все параметры имеют допустимые значения по умолчанию, отчет запускается автоматически при первом просмотре.  
  
 Параметры отчета могут представлять одно или несколько значений. В качестве одного значения можно указать литерал или выражение. При указании нескольких значений можно предоставить статический список или список из набора данных отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 После публикации отчета можно изменить значения по умолчанию, определяемые в отчете с помощью средства разработки отчетов, задавая значения свойств параметров на сервере отчетов. Для параметра можно также предоставить несколько наборов значений по умолчанию, создав связанные отчеты. Дополнительные сведения см. в разделе  [Report Parameters &#40;Report Builder and Report Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a>Добавление или изменение значений по умолчанию для параметра отчета  
  
1.  В области данных отчета разверните узел **Параметры** . Щелкните правой кнопкой мыши параметр и выберите команду **Изменить**. Откроется диалоговое окно **Свойства параметра отчета** .  
  
    > [!NOTE]  
    >  Если область данных отчета не появилась, в меню **Вид** выберите команду **Данные отчета**.  
  
2.  Нажмите кнопку **Значения по умолчанию**.  
  
3.  Выберите параметр по умолчанию.  
  
    -   Чтобы вручную указать значение или список значений, нажмите кнопку **Указать значения**. Нажмите кнопку **Добавить** и введите значение в текстовое поле **Значение** . Для значения можно записать выражение. Тип данных должен соответствовать типу данных параметра. Нельзя задавать параметры в выражении с помощью имен полей.  
  
         Для многозначных параметров повторите этот шаг нужное количество раз. Порядок, в котором значения отображаются в данном списке, определяет порядок, в котором пользователь увидит их в раскрывающемся списке. Чтобы изменить порядок элементов списка, щелкните текстовое поле **Значение** , чтобы выбрать элемент, а потом с помощью кнопок со стрелками вверх и вниз переместите выбранный элемент вверх или вниз по списку.  
  
    -   Чтобы предоставить имя существующего набора данных, получающего значения, щелкните **Получать значения из запроса**. В поле **Набор данных**введите имя набора данных.  
  
         В поле **Поле значения**выберите имя поля, которое предоставляет значения параметра.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a>Удаление значений по умолчанию для параметра отчета  
  
1.  В области данных отчета разверните узел **Параметры** . Щелкните правой кнопкой мыши параметр и выберите команду **Изменить**. Откроется диалоговое окно **Свойства параметра отчета** .  
  
2.  Нажмите кнопку **Значения по умолчанию**.  
  
3.  В области **Выберите один из следующих параметров**выберите **Нет значения по умолчанию**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Параметры отчета &#40; Построитель отчетов и конструктор отчетов &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Добавление каскадных параметров отчета &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Учебник: Добавление параметра к отчету &#40; Построитель отчетов &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Добавление фильтров набора данных, фильтров области данных и фильтры групп &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ссылки на коллекцию параметров &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Изменение порядка параметров отчета &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Добавить, изменить или удалить параметр отчета &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [Выражения &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  

