---
title: Определение операций со счетами (мастер бизнес-аналитики) | Документы Microsoft
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
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3b55d270b9b7ae2a2094c24e0f71bdcd0f72a0ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189633"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a>Определение логики операций со счетами (мастер бизнес-аналитики) 
  Используйте страницу **Определение логики операций со счетами** для сопоставления типов записей, определенных в экземпляре служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , с типами записей, заданных таблицей-источником в источнике данных, поставляющем данные для измерения счетов.  
  
> [!NOTE]  
>  Эта страница появится, если атрибут измерения будет сопоставлен **типу счета** на странице **Настройка атрибутов измерения** .  
  
## <a name="options"></a>Параметры  
 **Типы счетов исходной таблицы**  
 Отображает значения, которые содержатся в атрибуте измерения, назначенном типу атрибута **Тип счета** на странице **Настройка атрибутов измерения** .  
  
 **Встроенные типы счетов**  
 Выберите тип счета, определенный в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , который соответствует типам счетов записей таблицы-источника.  
  
 Следующая таблица содержит список типов счетов, определенных в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Актив**|Ценность вещей, находящихся в собственности в заданное время.|  
|**Баланс**|Итоговое количество чего-либо в заданное время.|  
|**Расход**|Ценность потраченного.|  
|**Поток**|Подсчет приращений элементов.|  
|**Доходы**|Ценность полученного.|  
|**Обязательство**|Ценность подлежащего возврату в заданное время.|  
|**Статистические**|Вычисленное соотношение или количество некоторой величины, не подлежащей статистической обработке.|  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера бизнес-аналитики](business-intelligence-wizard-f1-help.md)   
 [Конструктор кубов &#40;службы Analysis Services — многомерные данные&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Конструктор измерений &#40;службы Analysis Services — многомерные данные&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  