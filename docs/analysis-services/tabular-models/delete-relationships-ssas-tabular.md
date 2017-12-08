---
title: "Удаление связей (табличные службы SSAS) | Документы Microsoft"
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
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8c17aa3e6662d37dfb3863756597dd95022f7f02
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="delete-relationships-ssas-tabular"></a>Удаление связей (табличные службы SSAS)
  Удалять существующие связи можно с помощью конструктора моделей в представлении диаграмм или диалогового окна «Управление связями». Сведения об использовании связей в табличных моделях см. в разделе [Связи (табличные службы SSAS)](../../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
## <a name="considerations-for-deleting-relationships"></a>Замечания об удалении связей  
 Принимая решение об удалении связи, необходимо учитывать следующие моменты.  
  
-   Отменить удаление связи невозможно. Можно создать связь повторно, но это действие потребует полного пересчета формул в модели. Таким образом, перед удалением связи всегда нужно сначала проверить, не используется ли она в формулах.  
  
-   Удаление связи между двумя таблицами может привести к ошибкам в формулах, которые ссылаются на данные таблицы.  
  
-   Функция выражений анализа данных (DAX) RELATED использует связи между таблицами для поиска связанных значений в другой таблице. После удаления связи она будет возвращать другие результаты. Дополнительные сведения см. в описании функции RELATED (DAX).  
  
-   Помимо изменения результатов сводной таблицы и формулы, операции создания и удаления связей приводят к пересчету книги, что может занять некоторое время.  
  
## <a name="delete-relationships"></a>Удаление связей  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>Удаление связи с помощью представления диаграммы  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в меню **Модель** укажите **Представление модели**и выберите пункт **Представление диаграммы**.  
  
2.  Правой кнопкой мыши щелкните линию связи между двумя таблицами и выберите команду **Удалить**.  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>Удаление связи с помощью диалогового окна «Управление связями»  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]выберите меню **Таблица** и выберите команду **Управление связями**.  
  
2.  В диалоговом окне **Управление связями** выберите связи из списка.  
  
     Чтобы выбрать несколько связей, щелкните каждую из них, удерживая нажатой клавишу CTRL.  
  
3.  Нажмите кнопку **Удалить связь**.  
  
4.  В диалоговом окне **Управление связями** нажмите кнопку **Закрыть**.  
  
## <a name="see-also"></a>См. также  
 [Связи (табличные службы SSAS)](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [Создание связи между двумя таблицами (табличные службы SSAS)](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
