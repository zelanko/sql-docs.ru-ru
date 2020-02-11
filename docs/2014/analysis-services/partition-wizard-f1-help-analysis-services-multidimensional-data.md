---
title: Справка F1 мастера секционирования (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Partition Wizard
ms.assetid: 3b6d7053-aeef-4d9e-af70-f5b40256e859
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86976ac183fc592deab50ebdf5599ef3e7231c28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072124"
---
# <a name="partition-wizard-f1-help-analysis-services---multidimensional-data"></a>Справка F1 мастера секционирования (службы Analysis Services — многомерные данные)
  Мастер секционирования можно использовать для определения секций для группы мер в кубе. По умолчанию для каждой группы мер в кубе определяется одна секция. Для крупных секций, однако, могут снизиться меры доступа и производительности обработки. Создавая несколько секций, каждая из которых содержит часть данных для группы мер, можно улучшить показатели доступа и производительности обработки для данной группы мер.  
  
> [!CAUTION]  
>  Можно создать секции, которые будут содержать неверные данные, включив повторяющиеся строки на страницах **Определение исходных сведений** или **Ограничение на строки** .  
  
 Мастер секционирования проводит пользователя через следующую последовательность шагов.  
  
-   Выбор представления источников данных для секции.  
  
-   Создание фильтра для записей, включенных в секцию.  
  
-   Настройка расположения обработки и хранения.  
  
-   Присвоение имени и сохранение секции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Мастер определения источника &#40;секций&#41;](specify-source-information-partition-wizard.md)  
  
-   [Мастер секционирования ограничений строк &#40;&#41;](restrict-rows-partition-wizard.md)  
  
-   [Мастер создания секций и места хранения &#40;&#41;](processing-and-storage-locations-partition-wizard.md)  
  
-   [Завершение мастера создания разделов &#40;мастера&#41;](completing-the-wizard-partition-wizard.md)  
  
-   [Диалоговое окно «Выбор удаленной папки» &#40;Analysis Services многомерных данных&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a>См. также:  
 [Секции &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
