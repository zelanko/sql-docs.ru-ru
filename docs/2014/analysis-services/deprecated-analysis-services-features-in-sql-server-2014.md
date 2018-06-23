---
title: Устаревшие служб Analysis Services функции в SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 49a65a9ca1684a7bcec7b5f7f1d19d38b01f13d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098063"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a>Устаревшие функции служб Analysis Services в SQL Server 2014
  В этом разделе описаны устаревшие функции компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которые по-прежнему доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Функции, не поддерживаемые в следующей версии SQL Server  
 Следующие функции компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не будут поддерживаться в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются.  
  
|Категория|Устаревшая функция|Замена|  
|--------------|------------------------|-----------------|  
|Функция многомерных выражений|CalculationPassValue, функция|Нет. Механизм OLAP управляет этапом вычисления. Эта функция больше не нужна.|  
|Функция многомерных выражений|CalculationCurrentPass, функция|Нет. Механизм OLAP управляет этапом вычисления. Эта функция больше не нужна.|  
|Многомерные выражения.|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR была включена по умолчанию.|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR будет отключена по умолчанию в будущем выпуске. При неправильном использовании подсказка оптимизации многомерного выражения может выдавать неверные результаты.|  
|Другое|Внутреннее свойство ячейки CELL_EVALUATION_LIST|Первоначально предоставлялся список вычисляемых формул, применимых к ячейке. В данном выпуске Analysis Services это свойство пусто.  Порядок вычисления теперь указывается в скрипте многомерных выражений. Дополнительные сведения см. в разделе [основные сведения о порядке передачи и порядок вычислений &#40;многомерных Выражений&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|  
|Объекты|Сборки COM|Использование сборок COM может представлять угрозу безопасности. Поддержка сборок COM будет удалена в будущем выпуске.|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Функции, не поддерживаемые в будущей версии SQL Server  
 Поддержка приведенных ниже функций компонента [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , пока не определено).  
  
|Категория|Устаревшая функция|Замена|  
|--------------|------------------------|-----------------|  
|Многомерные модели|Удаленные секции|Нет. Вместо этого используйте локальные секции. В разделе [Создание и управление локальной секции &#40;служб Analysis Services&#41; ](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) для получения дополнительной информации.|  
|Многомерные модели|Удаленные связанные группы мер|Удаленная связанная группа мер ― это связанная группа мер, которая использует источник данных на удаленном сервере. Возможность связанной группы мер использовать удаленный источник данных будет планово выведена из эксплуатации.<br /><br /> Замены для этой функции нет. Вместо нее рекомендуется использовать локальные связанные группы мер. В разделе [связанные группы мер](multidimensional-models/linked-measure-groups.md) для получения дополнительной информации.|  
|Многомерные модели|Многомерная обратная запись|Нет. Если нужна возможность обратной записи, используйте обратную запись секции. В разделе [Set Partition Writeback](multidimensional-models/set-partition-writeback.md) для получения дополнительной информации.|  
|Многомерные модели|Связанные измерения|Нет. Можно скопировать измерения в другие модели, а не устанавливать связь с измерением из другой модели.|  
|Многомерное выражение|Свойство Non_Empty_Behavior|Нет. При создании вычисляемого элемента ошибочное задание этого свойства увеличивает вероятность возврата неверных результатов. В последних оптимизациях ядра OLAP улучшены операции с наборами разреженных данных, что делает это свойство менее релевантным.|  
  
## <a name="see-also"></a>См. также  
 [Обратная совместимость служб Analysis Services](analysis-services-backward-compatibility.md)   
 [Функции служб неподдерживаемые Analysis Services в SQL Server 2014](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  