---
title: "Создание ролей и управление ими (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 13aa039fc89a95af9f977c191ef90b624edb6b9c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-and-manage-roles-ssas-tabular"></a>Создание ролей и управление ими (табличные службы SSAS)
  В табличной модели роли определяют разрешения члена для модели. Роли определяются для проекта модели с помощью диалогового окна «Диспетчер ролей» в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. В развернутой модели администраторы баз данных могут управлять ролями с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Задачи в этом разделе описывают создание ролей и управление ролями во время создания модели с помощью диалогового окна «Диспетчер ролей» в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Сведения об управлении ролями в развернутой базе данных модели см. в разделе [Роли табличных моделей (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Задания  
 Создавать, изменять, копировать и удалять роли можно в диалоговом окне **Диспетчер ролей** . Чтобы открыть диалоговое окно **Диспетчер ролей** в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], выберите в меню **Модель** пункт **Диспетчер ролей**.  
  
###  <a name="bkmk_new_role"></a> Создание новой роли  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]откройте меню **Модель** и выберите команду **Диспетчер ролей**.  
  
2.  В диалоговом окне **Диспетчер ролей** выберите **Создать**.  
  
     В список ролей будет добавлена новая выделенная роль.  
  
3.  В списке **Роли** в поле **Имя** введите имя роли.  
  
     По умолчанию к имени роли, заданному по умолчанию, будет добавляться номер, последовательно увеличивающийся для каждой новой роли. Рекомендуется ввести имя, ясно определяющее тип члена, например «Финансовые менеджеры» или «Специалисты по кадрам».  
  
4.  В поле **Разрешения** щелкните стрелку вниз и выберите один из следующих типов разрешения.  
  
    |Разрешение|Description|  
    |----------------|-----------------|  
    |**Нет**|Члены не могут вносить изменения в схему модели и просматривать данные.|  
    |**Чтение**|Члены могут просматривать данные (с учетом фильтров строк), но не могут вносить изменения в схему модели.|  
    |**Чтение и обработка**|Члены могут просматривать данные (с учетом фильтров строк), а также выполнять операции «Обработать» и «Обработать все», но не могут вносить изменения в схему модели.|  
    |**Процесс**|Члены могут выполнять операции «Обработать» и «Обработать все». Не могут изменять схему модели и просматривать данные.|  
    |**Администратор**|Члены могут вносить изменения в схему модели и просматривать все данные.|  
  
5.  Чтобы ввести описание роли, щелкните поле **Описание** и введите описание.  
  
6.  Если у создаваемой роли есть разрешение «Чтение» или «Чтение и обработка», можно добавить фильтры строк с помощью формулы DAX. Чтобы добавить фильтры строк, перейдите на вкладку **Фильтры строк** , выберите таблицу, щелкните поле **Фильтр DAX** и введите формулу DAX.  
  
7.  Чтобы добавить членов роли, перейдите на вкладку **Члены** и нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  Членов роли также можно добавлять в развернутую модель с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Управление ролями с помощью среды SSMS (табличные службы SSAS)](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  В диалоговом окне **Выбор пользователей или групп** введите объекты пользователя или группы Windows в качестве членов.  
  
9. Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Роли (табличные службы SSAS)](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Перспективы (табличные службы SSAS)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Анализ в Excel &#40; Табличные службы SSAS &#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME, функция (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [CUSTOMDATA, функция (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  
