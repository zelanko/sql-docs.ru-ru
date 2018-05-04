---
title: Создание и управление ролями | Документы Microsoft
ms.custom: ''
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 50f1946d0a3a35b28635134547fd8e1053bb78e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-manage-roles"></a>Создание ролей и управление ими 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В табличной модели роли определяют разрешения члена для модели. Роли определяются для проекта модели с помощью диалогового окна «Диспетчер ролей» в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. В развернутой модели администраторы баз данных могут управлять ролями с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Задачи в этой статье описывается создание и управление ролями во время создания модели с помощью диалогового окна диспетчера ролей в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Сведения об управлении ролями в развернутой модели базы данных см. в разделе [табличной модели роли](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Задания  
 Создавать, изменять, копировать и удалять роли можно в диалоговом окне **Диспетчер ролей** . Чтобы открыть диалоговое окно **Диспетчер ролей** в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], выберите в меню **Модель** пункт **Диспетчер ролей**.  
  
###  <a name="bkmk_new_role"></a> Создание новой роли  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]откройте меню **Модель** и выберите команду **Диспетчер ролей**.  
  
2.  В диалоговом окне **Диспетчер ролей** выберите **Создать**.  
  
     В список ролей будет добавлена новая выделенная роль.  
  
3.  В списке **Роли** в поле **Имя** введите имя роли.  
  
     По умолчанию к имени роли, заданному по умолчанию, будет добавляться номер, последовательно увеличивающийся для каждой новой роли. Рекомендуется ввести имя, ясно определяющее тип члена, например «Финансовые менеджеры» или «Специалисты по кадрам».  
  
4.  В поле **Разрешения** щелкните стрелку вниз и выберите один из следующих типов разрешения.  
  
    |Разрешение|Описание|  
    |----------------|-----------------|  
    |**None**|Члены не могут вносить изменения в схему модели и просматривать данные.|  
    |**Чтение**|Члены могут просматривать данные (с учетом фильтров строк), но не могут вносить изменения в схему модели.|  
    |**Чтение и обработка**|Члены могут просматривать данные (с учетом фильтров строк), а также выполнять операции «Обработать» и «Обработать все», но не могут вносить изменения в схему модели.|  
    |**Процесс**|Члены могут выполнять операции «Обработать» и «Обработать все». Не могут изменять схему модели и просматривать данные.|  
    |**Администратор**|Члены могут вносить изменения в схему модели и просматривать все данные.|  
  
5.  Чтобы ввести описание роли, щелкните поле **Описание** и введите описание.  
  
6.  Если у создаваемой роли есть разрешение «Чтение» или «Чтение и обработка», можно добавить фильтры строк с помощью формулы DAX. Чтобы добавить фильтры строк, перейдите на вкладку **Фильтры строк** , выберите таблицу, щелкните поле **Фильтр DAX** и введите формулу DAX.  
  
7.  Чтобы добавить членов роли, перейдите на вкладку **Члены** и нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  Членов роли также можно добавлять в развернутую модель с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [управление ролями с помощью среды SSMS](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  В диалоговом окне **Выбор пользователей или групп** введите объекты пользователя или группы Windows в качестве членов.  
  
9. Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Роли](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Перспективы](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Анализ в Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME, функция (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [CUSTOMDATA, функция (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  
