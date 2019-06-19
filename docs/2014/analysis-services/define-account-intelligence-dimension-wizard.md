---
title: Определение операций со счетами (мастер измерений) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7bbc2b890c61e2864aa727f42276f01c87e94a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66082161"
---
# <a name="define-account-intelligence-dimension-wizard"></a>Определение логики операций со счетами (мастер измерений)
  Используйте страницу **Определение логики операций со счетами** , чтобы сопоставить типы счетов, определенные в экземпляре служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , с типами счетов, определенных в атрибуте измерения, связанном в измерении с типом атрибута **Тип счета** .  
  
> [!NOTE]  
>  Эта страница отображается, только если был выбран пункт **Стандартное измерение** на странице **Выбор типа измерения** и атрибут измерения был сопоставлен с типом атрибута **Тип счета** на странице **Определение типа измерения** .  
  
## <a name="options"></a>Параметры  
 **Типы счетов исходной таблицы**  
 Отображает значения, содержащиеся в атрибуте измерения, присвоенном типу атрибута **Тип счета** на странице **Определение ключа и типа измерения** .  
  
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
 [Справка F1 мастера измерений](dimension-wizard-f1-help.md)   
 [Измерения &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
