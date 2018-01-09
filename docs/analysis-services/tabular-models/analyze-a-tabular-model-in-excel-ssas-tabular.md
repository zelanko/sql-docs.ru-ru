---
title: "Анализ табличной модели в Excel (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 57bcb66a1533cc56493f561ab81b2ccbade96eb7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Анализ табличной модели в Excel (табличные службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Функция анализа в Excel в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] открывает Microsoft Excel, создает соединение с источником данных для базы данных рабочей области модели, и добавляет сводную таблицу на лист. Объекты модели (таблицы, столбцы, меры, иерархии и ключевые показатели эффективности) включаются в качестве полей в список полей сводной таблицы.  
  
> [!NOTE]  
>  Для использования функции анализа в Excel необходимо на тот же компьютер, где находится среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], установить Microsoft Office 2003 или более поздней версии. Если Microsoft Office не установлен на том же компьютере, то можно с помощью Excel на другом компьютере подключиться к базе данных рабочей области модели в качестве источника данных. Затем можно вручную добавить сводную таблицу на лист. Объекты модели (таблицы, столбцы, меры и ключевые показатели эффективности) включаются в качестве полей в список полей сводной таблицы.  
  
## <a name="tasks"></a>Задания  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>Анализ проекта табличной модели с помощью функции анализа в Excel  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]щелкните меню **Модель** и выберите пункт **Анализ в Excel**.  
  
2.  В диалоговом окне **Выбор учетных данных и перспективы** выберите один из приведенных ниже вариантов учетных данных для подключения к источнику данных рабочей области модели:  
  
    -   Для использования текущей учетной записи пользователя выберите **Текущий пользователь Windows**.  
  
    -   Чтобы воспользоваться другой учетной записью, выберите **Другой пользователь Windows**.  
  
         Обычно эта учетная запись будет членом той или иной роли. Пароль не требуется. Эта учетная запись может использоваться только в контексте подключения Excel к базе данных рабочей области.  
  
    -   Чтобы воспользоваться ролью безопасности, выберите **Роль**, а затем в поле со списком выберите одну или несколько ролей.  
  
         Роли безопасности должны определяться с помощью диспетчера ролей. Дополнительные сведения см. в разделе [Создание ролей и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
3.  Чтобы воспользоваться перспективой, выберите нужную в поле со списком **Перспектива** .  
  
     Перспективы (за исключением заданных по умолчанию) должны определяться в диалоговом окне «Перспективы». Дополнительные сведения см. в разделе [Создание перспектив и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  Список полей сводной таблицы в Excel не обновляется автоматически при внесении изменений в проект модели в конструкторе моделей. Чтобы обновить список полей сводной таблицы в Excel, нажмите кнопку **Обновить** на ленте **Параметры**.  
  
## <a name="see-also"></a>См. также:  
 [Анализ в Excel (табличные службы SSAS)](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
