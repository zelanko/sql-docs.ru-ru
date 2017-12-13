---
title: "Использование ДЕТАЛИЗАЦИИ для извлечения исходных данных (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 30587e46a4ac54d2ac2825649f25cb321c05eba4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>Управление данными MDX - получение источника данных с помощью функции DRILLTHROUGH
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Использует многомерных выражений (MDX) [ДЕТАЛИЗАЦИИ](../../../mdx/mdx-data-manipulation-drillthrough.md)инструкции для извлечения набора строк из источника данных для ячейки куба.  
  
 Чтобы в кубе можно было выполнять инструкцию **DRILLTHROUGH** , для него следует определить действие детализации. Чтобы определить действие детализации, в конструкторе кубов в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]на панели **Действия** выберите на панели инструментов пункт **Создать действие детализации**. Для действия детализации укажите имя, цель и условие действия, а также столбцы, возвращаемые инструкцией **DRILLTHROUGH** .  
  
## <a name="drillthrough-statement-syntax"></a>Синтаксис инструкции DRILLTHROUGH  
 Синтаксис инструкции **DRILLTHROUGH** :  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 Предложение **SELECT** определяет ячейку куба, содержащую извлекаемые исходные данные. Это предложение **SELECT** эквивалентно обычной инструкции многомерных выражений **SELECT** , за исключением того, что в предложении **SELECT** на каждой оси можно указывать только один элемент. Если на оси указано несколько элементов, возникает ошибка.  
  
 Синтаксическая конструкция `<Max_Rows>` задает максимальное количество строк в каждом возвращаемом наборе строк. Если поставщик OLE DB, используемый для соединения с источником данных, не поддерживает параметр **DBPROP_MAXROWS**, аргумент `<Max_Rows>` не учитывается.  
  
 Синтаксическая конструкция `<First_Rowset>` определяет секцию, набор строк которой возвращается первым.  
  
 Синтаксическая конструкция `<Return_Columns>` определяет возвращаемые столбцы базовой базы данных.  
  
## <a name="drillthrough-statement-example"></a>Пример инструкции DRILLTHROUGH  
 В следующем примере иллюстрируется использование инструкции **DRILLTHROUGH** . В этом примере инструкция DRILLTHROUGH обращается с запросом к концевым элементам измерений Store, Product и Time вдоль измерения Stores (ось среза) и возвращает группу мер Department, идентификатор отдела и имя сотрудника.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>См. также  
 [Манипулирование данными (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
