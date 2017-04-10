---
title: "Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.loaddimwizard.scdsupport.f1"
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений)
  Диалоговое окно **Столбцы медленно меняющихся измерений** используется для выбора типа изменения для каждого столбца медленно меняющихся измерений.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## Параметры  
 **Столбцы измерений**  
 Выберите столбец измерения из списка.  
  
 **Тип изменения**  
 Выберите пункт **Атрибут неизменности** или один из двух типов изменяющихся атрибутов. Используйте пункт **Атрибут неизменности** , когда значение в столбце не должно изменяться; службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] тогда будут воспринимать изменения как ошибки. Используйте **Изменяемый атрибут** для замены существующих значений измененными значениями. Используйте **Атрибут c предысторией** для сохранения измененных значений в новых записях с пометкой предыдущих записей как устаревших.  
  
 **Удалить**  
 Выберите столбец измерения и удалите его из списка сопоставленных столбцов, нажав кнопку **Удалить**.  
  
## См. также  
 [Настройка выходов при помощи мастера медленно изменяющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  