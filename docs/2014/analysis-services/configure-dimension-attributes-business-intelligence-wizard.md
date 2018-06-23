---
title: Настройка атрибутов измерения (мастер бизнес-аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e9ce0f7535f111d5c9152304a4e27315f73e5087
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110057"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a>Настройка атрибутов измерения (мастер бизнес-аналитики)
  Страница **Настройка атрибутов измерения** используется для сопоставления атрибутов измерения с типами атрибутов, используемыми службами [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для идентификации атрибутов для измерений счетов.  
  
## <a name="options"></a>Параметры  
 **Тип измерения**  
 Отображает выбранный тип измерения.  
  
> [!NOTE]  
>  Этот параметр недоступен из-за `Type` измерения нельзя добавить значение отличное от *учетной записи* для измерений счетов.  
  
 **Атрибуты измерения**  
 Отображает допустимые типы атрибутов, которые можно сопоставить с существующими атрибутами измерений в измерении.  
  
 **Включить**  
 Установите флажок для включения соответствующего типа атрибута в измерение.  
  
 **Тип атрибута**  
 Отображает список типов атрибутов, которые можно сопоставить с существующими атрибутами измерений в измерении.  
  
 **Атрибут измерения**  
 Выберите атрибут измерения, который необходимо сопоставить с нужным типом атрибутов.  
  
 **Установить полуаддитивные меры в зависимости от типа учетной записи**  
 Выберите, чтобы каждая мера, связанная с данным измерением, агрегировалась по типу счета.  
  
> [!NOTE]  
>  Этот параметр не отображается, если мастер бизнес-аналитики был запущен из конструктора измерений, а также при щелчке правой кнопкой мыши по измерению в обозревателе решений в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера бизнес-аналитики](business-intelligence-wizard-f1-help.md)   
 [Конструктор кубов &#40;службы Analysis Services — многомерные данные&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Конструктор измерений &#40;службы Analysis Services — многомерные данные&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  