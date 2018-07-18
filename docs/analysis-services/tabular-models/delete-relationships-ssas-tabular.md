---
title: Удаление связей | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 115d72bd0b833d1f392b2349d3ed4e4970f58453
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37999183"
---
# <a name="delete-relationships"></a>Удаление связей 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Удалять существующие связи можно с помощью конструктора моделей в представлении диаграмм или диалогового окна «Управление связями». Сведения об использовании связей в табличных моделях см. в разделе [связи](../../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
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
 [Связи](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [Создание связи](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
