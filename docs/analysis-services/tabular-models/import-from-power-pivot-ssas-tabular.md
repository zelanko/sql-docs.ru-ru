---
title: "Импорт из Power Pivot (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b85ae04b00034decd7390f86db1ee7e00c496434
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="import-from-power-pivot-ssas-tabular"></a>Импорт из Power Pivot (табличные службы SSAS)
  В данном разделе описано создание нового проекта табличной модели при помощи импорта метаданных и данных из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] с использованием шаблона проекта "Импорт из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] " в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-tabular-model-from-a-power-pivot-for-excel-file"></a>Создание новой табличной модели из файла Power Pivot для Excel  
 Метаданные, импортируемые из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] при создании нового проекта табличной модели и определяющие структуру книги, используются для создания и определения структуры проекта табличной модели в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Такие объекты, как таблицы, столбцы, меры и связи, сохраняются, а затем появляются в проекте табличной модели, как в книге [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Изменения в файл книги XLSX не вносятся.  
  
> [!NOTE]  
>  Связанные таблицы не поддерживаются в табличных моделях. При импорте связанных таблиц из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] данные из них обрабатываются как вставленные с помощью операции копирования и вставки и сохраняются в файле Model.bim. При просмотре свойств таблицы, вставленной с помощью операции копирования и вставки, свойство **Исходные данные** и диалоговое меню **Свойства таблицы** в меню **Таблица** отключены.  
>   
>  Существует ограничение в 10 000 строк, которые можно добавить к данным, внедренным в модель. Если при импорте модели из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] отображается ошибка "Данные усечены. Вставленные таблицы не могут содержать более 10000 строк", то необходимо исправить модель [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , переместив внедренные данные в другой источник данных, например таблицу SQL Server, а затем выполнив повторный импорт.  
  
 В зависимости от того, находится база данных рабочей области в экземпляре служб Analysis Services, расположенном на одном компьютере (локальном) со средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , или на удаленном экземпляре служб Analysis Services, нужно учитывать особые требования.  
  
 Если база данных рабочей области находится в локальном экземпляре служб Analysis Services, то из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] можно импортировать и метаданные, и данные. Метаданные копируются из книги и используются для создания проекта табличной модели. Затем данные копируются из книги и сохраняются в базу данных рабочей области проекта (за исключением данных копирования и вставки, которые сохраняются в файл Model.bim).  
  
 Если база данных рабочей области находится на удаленном экземпляре служб Analysis Services, то импортировать данные из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel нельзя. Метаданные при этом импортировать можно, однако в этом случае скрипт будет выполняться на удаленном экземпляре служб Analysis Services. Метаданные следует импортировать только из доверенных книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Данные должны быть повторно импортированы из источников, определенных в подключениях к источнику данных. Скопированные и вставленные, а также связанные табличные данные из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] необходимо скопировать и вставить в проект табличной модели.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-power-pivot-for-excel-file"></a>Создание нового проекта табличной модели из файла Power Pivot для Excel  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]в меню **Файл** выберите пункт **Создать**, а затем выберите пункт **Проект**.  
  
2.  В диалоговом окне **Создание проекта** выберите в разделе **Установленные шаблоны** пункт **Бизнес-аналитика**, затем нажмите кнопку **Импортировать из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
3.  В поле  **Имя**введите имя проекта, укажите расположение и имя решения, а затем нажмите кнопку **ОК**.  
  
4.  В диалоговом окне **Открыть** выберите файл [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] , содержащий необходимые для импорта метаданные модели и данные, и нажмите кнопку **Открыть**.  
  
## <a name="see-also"></a>См. также  
 [База данных рабочей области (табличные службы SSAS)](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)   
 [Копирование и вставка данных &#40; Табличные службы SSAS &#41;](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)  
  
  
