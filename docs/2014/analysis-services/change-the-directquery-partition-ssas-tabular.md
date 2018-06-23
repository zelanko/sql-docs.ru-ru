---
title: Изменение секции DirectQuery (табличные службы SSAS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5c777c0ce70d06b979fbc26ac8f50df1bdbd858d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188127"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a>Изменение секции DirectQuery (табличные службы SSAS)
  Поскольку только одну секцию в таблице можно определить как секцию DirectQuery, службы Analysis Services по умолчанию используют первую секцию, созданную в таблице. При создании проекта модели секцию DirectQuery можно изменять с помощью диалогового окна «Диспетчер секций» в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Для развернутых моделей изменить секцию DirectQuery можно с помощью среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a>Изменение секции DirectQuery для проекта табличной модели  
  
1.  В конструкторе моделей в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]щелкните таблицу (вкладку), содержащую секционированную таблицу.  
  
2.  В меню **Таблица** выберите **Секции**.  
  
3.  В **диспетчере секций**секцией является текущая секция DirectQuery, имя которой содержит префикс **(DirectQuery)** .  
  
     Выберите другую секцию в списке **Секции** , затем выберите **Установить в качестве DirectQuery**. Кнопка **Установить в качестве DirectQuery** неактивна, если выбрана текущая секция DirectQuery, и не отображается, если в модели не поддерживается режим прямых запросов.  
  
4.  При необходимости измените параметры обработки и нажмите кнопку **ОК**.  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a>Изменение секции DirectQuery для развернутой табличной модели  
  
1.  В [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]откройте шаблон базы данных в обозревателе объектов.  
  
2.  Разверните узел **Таблицы** , щелкните правой кнопкой мыши секционированную таблицу и выберите команду **Секции**.  
  
     Имя секции, определенной для использования в режиме DirectQuery, имеет префикс (DirectQuery).  
  
3.  Чтобы перейти к другой секции, щелкните значок **Прямой запрос** на панели инструментов, чтобы открыть диалоговое окно **Настройка секции DirectQuery** . Значок панели инструментов DirectQuery недоступен в моделях, не поддерживающих прямые запросы.  
  
4.  Выберите другую секцию в раскрывающемся списке **Имя секции** и при необходимости измените параметры обработки.  
  
## <a name="see-also"></a>См. также  
 [Секции &#40;табличные службы SSAS&#41;](tabular-models/partitions-ssas-tabular.md)  
  
  