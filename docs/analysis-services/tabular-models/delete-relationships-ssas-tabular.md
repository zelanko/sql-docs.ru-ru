---
title: "Удаление связей (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: 4ab9e8b9845b77601b2ea1a5d39cd7f81a48e326
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="delete-relationships-ssas-tabular"></a>Удаление связей (табличные службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Существующие связи можно удалить с помощью конструктора моделей в представлении диаграммы или с помощью диалогового окна «Управление связями». Сведения об использовании связей в табличных моделях см. в разделе [Связи (табличные службы SSAS)](../../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
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
  
  
