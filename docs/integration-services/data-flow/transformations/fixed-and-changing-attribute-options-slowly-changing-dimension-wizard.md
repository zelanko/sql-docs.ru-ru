---
title: Параметры атрибутов неизменности и изменяемых атрибутов (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e54fc003f2bb61a5e94f521ddb1a0221261610e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71291429"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Параметры атрибутов неизменности и изменяемых атрибутов (мастер медленно изменяющихся измерений)

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В диалоговом окне **Параметры атрибутов неизменности и изменяемых атрибутов** можно определить реакцию на изменения фиксированных и изменяемых атрибутов.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Атрибуты неизменности**  
 Для атрибутов неизменности определяет, должна ли задача закончиться неудачей, если обнаружено изменение в атрибуте неизменности.  
  
 **Изменяемые атрибуты**  
 Для изменяемых атрибутов определяет, должна ли задача изменить все устаревшие записи или записи с истекшим сроком действия, в дополнение к текущим, при обнаружении изменения в изменяемом атрибуте. Записью с истекшим сроком действия является та, которая была заменена более новой записью в результате изменения атрибута с предысторией (изменение типа 2). Выбор этого параметра может наложить дополнительные требования к обработке в многомерном объекте, созданном в реляционном хранилище данных.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов с помощью мастера медленно изменяющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
