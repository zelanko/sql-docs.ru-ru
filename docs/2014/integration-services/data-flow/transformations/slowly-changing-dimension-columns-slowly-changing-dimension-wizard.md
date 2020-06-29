---
title: Столбцы медленно изменяющихся измерений (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6283887cbddb9844e0ac769281184f588dc2a94d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430261"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений)
  Диалоговое окно **Столбцы медленно меняющихся измерений** используется для выбора типа изменения для каждого столбца медленно меняющихся измерений.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Столбцы измерений**  
 Выберите столбец измерения из списка.  
  
 **Тип изменения**  
 Выберите пункт **Атрибут неизменности**или один из двух типов изменяющихся атрибутов. Используйте пункт **Атрибут неизменности** , когда значение в столбце не должно изменяться; службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] тогда будут воспринимать изменения как ошибки. Используйте **Изменяемый атрибут** для замены существующих значений измененными значениями. Используйте **Атрибут c предысторией** для сохранения измененных значений в новых записях с пометкой предыдущих записей как устаревших.  
  
 **Удалить**  
 Выберите столбец измерения и удалите его из списка сопоставленных столбцов, нажав кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов с помощью мастера медленно изменяющихся измерений](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
