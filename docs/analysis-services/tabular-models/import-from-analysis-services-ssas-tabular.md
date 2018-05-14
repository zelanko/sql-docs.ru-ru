---
title: Импорт из служб Analysis Services | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 625ac4fb1bf7c09aa0cfa651e105b6621e5be4b8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="import-from-analysis-services"></a>Импорт из служб Analysis Services 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В этой статье описывается создание нового проекта табличной модели путем импорта метаданных из существующей табличной модели с помощью функции импорта из шаблона проекта сервера в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Создание новой модели путем импорта метаданных из существующей модели в службах Analysis Services  
 Можно использовать шаблон проекта «Импорт с сервера» для создания нового проекта табличной модели с помощью копирования метаданных из существующей табличной модели с сервера служб Analysis Services. Новый проект будет содержать в себе те же соединения с источниками данных, таблицы, связи, меры, ключевые показатели эффективности, роли, иерархии, перспективы и секции, что и модель, используемая для импорта. Однако данные из существующей модели при этом не копируются в рабочую область новой модели. По завершении импорта, как только будет создан новый проект модели, необходимо запустить полную обработку для загрузки данных из источников данных в базу данных рабочей области нового проекта модели.  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>Создание новой модели путем импорта метаданных из существующей модели  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]в меню **Файл** выберите пункт **Создать**, а затем выберите пункт **Проект**.  
  
2.  В диалоговом окне **Создание проекта** выберите в разделе **Установленные шаблоны**пункт **Бизнес-аналитика**, затем нажмите кнопку **Импортировать с сервера**.  
  
3.  В поле **Имя**введите имя проекта, укажите расположение и имя решения, а затем нажмите кнопку **ОК**.  
  
4.  В диалоговом окне **Импорт из служб Analysis Services** в поле **Имя сервера**введите имя сервера служб Analysis Services, на котором находятся метаданные модели для импорта.  
  
5.  В поле **Имя базы данных**выберите базу данных табличной модели, содержащую метаданные модели для импорта, и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Свойства проекта](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  
