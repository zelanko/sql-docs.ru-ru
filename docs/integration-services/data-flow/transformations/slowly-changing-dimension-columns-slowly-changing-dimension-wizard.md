---
description: Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений)
title: Столбцы медленно изменяющихся измерений (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b27c9c0e575775449d2f3a25c5a20bd6667b5cd
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88425726"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений)

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Диалоговое окно **Столбцы медленно меняющихся измерений** используется для выбора типа изменения для каждого столбца медленно меняющихся измерений.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Столбцы измерений**  
 Выберите столбец измерения из списка.  
  
 **Тип изменения**  
 Выберите пункт **Атрибут неизменности** или один из двух типов изменяющихся атрибутов. Используйте пункт **Атрибут неизменности** , когда значение в столбце не должно изменяться; службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] тогда будут воспринимать изменения как ошибки. Используйте **Изменяемый атрибут** для замены существующих значений измененными значениями. Используйте **Атрибут c предысторией** для сохранения измененных значений в новых записях с пометкой предыдущих записей как устаревших.  
  
 **Удалить**  
 Выберите столбец измерения и удалите его из списка сопоставленных столбцов, нажав кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов при помощи мастера медленно изменяющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
