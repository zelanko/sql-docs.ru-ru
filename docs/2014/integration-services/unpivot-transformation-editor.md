---
title: Редактор преобразования «Отмена сведения» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
caps.latest.revision: 34
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2864345230b02bc16756c82116dc40a53b2a7264
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199664"
---
# <a name="unpivot-transformation-editor"></a>Редактор преобразования «Отмена свертывания»
  Используйте диалоговое окно **Редактор преобразования «Отмена свертывания»** , чтобы выбрать столбцы для сведения в строки, а также указать столбцы данных и новый выходной столбец сведенных значений.  
  
> [!NOTE]  
>  Этот раздел опирается на сценарий отмены свертывания, описанный в разделе [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) , чтобы проиллюстрировать использование параметров.  
  
 Дополнительные сведения о преобразовании отмены свертывания см. в разделе [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Используя флажки, укажите столбцы, которые должны быть сведены в строки.  
  
 **Название**  
 Просмотрите имя доступного входного столбца.  
  
 **Передать**  
 Укажите, следует ли включить этот столбец в выход с отмененным сведением.  
  
 **Входной столбец**  
 Выберите для каждой строки столбец из списка доступных входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы** .  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), входными столбцами являлись столбцы **Ham**, **Soda**, **Milk**, **Beer**и **Chips** .  
  
 **Целевой столбец**  
 Введите имя столбца данных.  
  
 В сценарии отмены свертывания, описанном в разделе [Преобразование отмены свертывания](data-flow/transformations/unpivot-transformation.md), целевым столбцом является столбец количества (**Qty**).  
  
 **Значение ключа сведения**  
 Введите имя значения сведения. По умолчанию, используется имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), значения сведения представлены в новом столбце Product, обозначенном параметром **Имя столбца значений ключа сведения** , в виде текстовых значений **Ham**, **Soda**, **Milk**, **Beer**и **Chips**.  
  
 **Имя столбца значений ключа сведения**  
 Введите имя столбца значений ключа сведения. По умолчанию, используется «Значение ключа сведения», тем не менее можно выбрать любое уникальное описательное имя.  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), именем столбца значений ключа сведения является **Product** , оно обозначает новый столбец **Product** , в который осуществляется отмена свертывания столбцов **Ham**, **Soda**, **Milk**, **Beer**и **Chips** .  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование "Сведение"](data-flow/transformations/pivot-transformation.md)  
  
  
