---
title: "Создание учетной записи Finance измерением типа родители потомки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1f4006934f9c92e492a984b02de9e585ec8ee84b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>Измерения базы данных — процент учетной записи типа родители потомки
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]измерением типа счета называют измерение, атрибуты которого представляют диаграмму счетов для целей финансовой отчетности.  
  
 Измерение счетов позволяет выборочно управлять поведением статистической обработки счетов во времени. Измерение счетов также позволяет использовать стандартный механизм разрешения большинства нестандартных проблем, связанных со статистическими выражениями, которые часто возникают в решениях бизнес-аналитики, обрабатывающих финансовые данные. Если такого стандартного механизма нет, то для решения нестандартных проблем, связанных со статистической обработкой, потребуются пользовательские формулы свертки, вычисляемые элементы или скрипты многомерных выражений.  
  
 Чтобы сделать измерение измерением счетов, установите для свойства **Type** этого измерения значение **Accounts**.  
  
## <a name="dimension-structure"></a>Структура измерения  
 Измерения счетов содержат не менее двух атрибутов:  
  
-   ключевой атрибут, определяющий отдельные счета в таблице измерения;  
  
-   атрибут счета — родительский атрибут, описывающий, каким образом устроена иерархия счетов в измерении.  
  
     Чтобы сделать атрибут атрибутом счета, присвойте свойству **Type** атрибута значение **Account** , а свойству **Usage** — значение **Parent**.  
  
 Измерения счетов могут содержать следующие атрибуты:  
  
-   атрибут типа счета определяет тип каждого счета измерения. Имена элементов атрибутов счета сопоставляются с типами счетов, которые определены для проекта или базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и обозначают статистическую функцию, применяемую службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для этих счетов. Для определения поведения статистических вычислений атрибутов счетов можно использовать унарные операторы и формулы пользовательской свертки, однако типы счетов позволяют легко добиться согласованного поведения диаграммы счетов без изменения исходной реляционной базы данных.  
  
     Чтобы определить атрибут счета, установите для свойства **Type** этого атрибута значение **AccountType**;  
  
-   атрибут имени счета применяется при построении отчетов. Чтобы определить атрибут имени счета, установите для свойства **Type** этого атрибута значение **AccountName**;  
  
-   атрибут номера счета применяется при построении отчетов. Чтобы определить атрибут номера счета, установите для свойства **Type** этого атрибута значение **AccountNumber**.  
  
 Дополнительные сведения о типах атрибутов см. в разделе [Настройка типов атрибутов](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Добавление логики операций со счетами при помощи мастера бизнес-аналитики  
 После определения измерения счетов и добавления измерения в куб можно добавить логику операций со счетами, например определение и сопоставление типов счетов, в измерение при помощи мастера бизнес-аналитики. Дополнительные сведения см. в разделе [Добавление логики операций со счетами к измерению](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Справка F1 мастера бизнес-аналитики](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Типы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  

