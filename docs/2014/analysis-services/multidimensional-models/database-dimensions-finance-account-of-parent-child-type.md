---
title: Создание учетной записи Finance измерением типа родители потомки | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
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
manager: mblythe
ms.openlocfilehash: 209184ce52888c65dc24c044517ccaf95d1a1a24
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086749"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a>Создание учетной записи Finance с измерением типа «родитель-потомок»
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]измерением типа счета называют измерение, атрибуты которого представляют диаграмму счетов для целей финансовой отчетности.  
  
 Измерение счетов позволяет выборочно управлять поведением статистической обработки счетов во времени. Измерение счетов также позволяет использовать стандартный механизм разрешения большинства нестандартных проблем, связанных со статистическими выражениями, которые часто возникают в решениях бизнес-аналитики, обрабатывающих финансовые данные. Если такого стандартного механизма нет, то для решения нестандартных проблем, связанных со статистической обработкой, потребуются пользовательские формулы свертки, вычисляемые элементы или скрипты многомерных выражений.  
  
 Чтобы определить измерение как измерение счетов, установите `Type` свойство измерения, `Accounts`.  
  
## <a name="dimension-structure"></a>Структура измерения  
 Измерения счетов содержат не менее двух атрибутов:  
  
-   ключевой атрибут, определяющий отдельные счета в таблице измерения;  
  
-   атрибут счета — родительский атрибут, описывающий, каким образом устроена иерархия счетов в измерении.  
  
     Чтобы определить атрибут как атрибут счета, установите `Type` свойства атрибута для `Account` и `Usage` свойства `Parent`.  
  
 Измерения счетов могут содержать следующие атрибуты:  
  
-   атрибут типа счета определяет тип каждого счета измерения. Имена элементов атрибутов счета сопоставляются с типами счетов, которые определены для проекта или базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и обозначают статистическую функцию, применяемую службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для этих счетов. Для определения поведения статистических вычислений атрибутов счетов можно использовать унарные операторы и формулы пользовательской свертки, однако типы счетов позволяют легко добиться согласованного поведения диаграммы счетов без изменения исходной реляционной базы данных.  
  
     Чтобы определить атрибут счета, установите для свойства `Type` этого атрибута значение `AccountType`;  
  
-   атрибут имени счета применяется при построении отчетов. Чтобы определить атрибут имени счета, установите для свойства `Type` этого атрибута значение `AccountName`;  
  
-   атрибут номера счета применяется при построении отчетов. Чтобы определить атрибут номера счета, установите `Type` свойства атрибута для `AccountNumber`.  
  
 Дополнительные сведения о типах атрибутов см. в разделе [Настройка типов атрибутов](attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Добавление логики операций со счетами при помощи мастера бизнес-аналитики  
 После определения измерения счетов и добавления измерения в куб можно добавить логику операций со счетами, например определение и сопоставление типов счетов, в измерение при помощи мастера бизнес-аналитики. Дополнительные сведения см. в разделе [Добавление логики операций со счетами к измерению](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Справка F1 мастера бизнес-аналитики](../business-intelligence-wizard-f1-help.md)   
 [Типы измерений](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  