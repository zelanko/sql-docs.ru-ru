---
title: Использование ДЕТАЛИЗАЦИИ для извлечения исходных данных (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 81c873d0ea6e5c21d97fc719ce1c72a773df43e5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>Управление данными MDX - получение источника данных с помощью функции DRILLTHROUGH
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В языке многомерных выражений для извлечения набора строк из источника данных для ячейки куба используется инструкция [DRILLTHROUGH](../../../mdx/mdx-data-manipulation-drillthrough.md).  
  
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
 [Обработка данных & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
