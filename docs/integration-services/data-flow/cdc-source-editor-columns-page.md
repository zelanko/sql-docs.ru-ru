---
title: "Редактор источника «CDC» (страница «столбцы») | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c746e2b90c9f4f2fc34a9285cf05612302e5c588
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="cdc-source-editor-columns-page"></a>Редактор источника «CDC» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор источника CDC** используется для сопоставления выходного столбца с каждым внешним (исходным) столбцом.  
  
 Дополнительные сведения об источнике CDC см. в разделе [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Список задач  
 **Открытие страницы «Столбцы» редактора источника CDC**  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]откройте пакет служб [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , содержащий источник CDC.  
  
2.  На вкладке **Поток данных** дважды щелкните источник CDC.  
  
3.  В окне **Редактор источника CDC**нажмите кнопку **Столбцы**.  
  
## <a name="options"></a>Параметры  
 **Доступные внешние столбцы**  
 Список доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы. Выберите используемые столбцы источника. Выбранные столбцы добавляются в список **Внешний столбец** в порядке выбора.  
  
 **Внешний столбец**  
 Представление внешних (исходных) столбцов в порядке, заданном при настройке компонентов, которые обрабатывают данные из источника CDC. Чтобы изменить этот порядок, снимите флажки для выбранных столбцов в списке **Доступные внешние столбцы** , а затем выберите внешние столбцы в другом порядке. Выбранные столбцы добавляются в список **Внешний столбец** в порядке выбора.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, но можно выбрать любое уникальное описательное имя. Введенное имя отображается в конструкторе служб SSIS.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника CDC &#40; Страницы диспетчера соединений &#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [Редактор источника CDC &#40; Страница «Вывод ошибок» &#41;](../../integration-services/data-flow/cdc-source-editor-error-output-page.md)  
  
  
