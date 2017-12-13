---
title: "Определение упорядочивания для измерения | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1b37dde7f32df56fdea9cb595796948f710a652f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="bi-wizard---define-the-ordering-for-a-dimension"></a>Мастер бизнес-Аналитики — определение упорядочивания для измерения
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Добавьте расширение к кубу или измерению, чтобы указать, как упорядочиваются элементы атрибута упорядочивания атрибутов. Элементы можно упорядочивать по имени или ключу атрибута, либо по имени или ключу другого атрибута (основанному на связи атрибута). По умолчанию элементы упорядочиваются по имени. Это расширение изменяет настройки свойств **OrderBy** и **OrderByAttributeID** для атрибутов в измерении.  
  
 Чтобы добавить упорядочивание атрибутов, используйте мастер бизнес-аналитики и выберите параметр **Задать сортировку атрибута** на странице **Выбор расширения** . После этого мастер отобразит шаги, позволяющие выбрать измерение, к которому необходимо применить упорядочивание атрибутов, и указать способ упорядочивания атрибутов для выбранного измерения.  
  
## <a name="selecting-a-dimension"></a>Выбор измерения  
 На первой странице **Определение порядка атрибутов** мастера указывается измерение, к которому необходимо применить упорядочивание атрибутов. Добавление расширения упорядочивания атрибутов к этому выбранному измерению приведет к изменению измерения. Эти изменения будут наследоваться всеми кубами, включающими выбранное измерение.  
  
## <a name="specifying-ordering"></a>Указание упорядочивания  
 На второй странице **Определение порядка атрибутов** мастера указывается, как будут упорядочиваться все атрибуты в измерении.  
  
 В столбце **Атрибут сортировки** можно изменить атрибут, используемый для выполнения упорядочивания. Если атрибут, который вы хотите использовать для упорядочивания элементов не находится в списке, прокрутите список вниз, а затем выберите  **\<создать атрибут... >** Открытие **выберите столбец** диалоговое окно, где это возможно Выберите столбец в таблице измерения. При выборе столбца с использованием диалогового окна **Выбор столбца** создается дополнительный атрибут, с помощью которого необходимо упорядочивать элементы атрибута.  
  
 В столбце **Критерии** после этого можно выбрать, необходимо ли упорядочивать элементы атрибута по **Key** или **Name**.  
  
  
