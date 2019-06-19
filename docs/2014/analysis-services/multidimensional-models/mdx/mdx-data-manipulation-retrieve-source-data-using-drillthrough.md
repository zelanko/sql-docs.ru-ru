---
title: С помощью функции DRILLTHROUGH извлечение данных из источника (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b437016cc29b2e4a85f781e3a422fb40c70f37c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074301"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a>Извлечение данных из источника с помощью функции DRILLTHROUGH (многомерные выражения)
  В языке многомерных выражений для извлечения набора строк из источника данных для ячейки куба используется инструкция [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough).  
  
 Чтобы в кубе можно было выполнять инструкцию `DRILLTHROUGH`, для него следует определить действие детализации. Чтобы определить действие детализации, в конструкторе кубов в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]на панели **Действия** выберите на панели инструментов пункт **Создать действие детализации**. Для действия детализации укажите имя, цель и условие действия, а также столбцы, возвращаемые инструкцией `DRILLTHROUGH`.  
  
## <a name="drillthrough-statement-syntax"></a>Синтаксис инструкции DRILLTHROUGH  
 Синтаксис инструкции `DRILLTHROUGH`:  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 Предложение `SELECT` определяет ячейку куба, содержащую извлекаемые исходные данные. Это предложение `SELECT` эквивалентно обычной инструкции многомерных выражений `SELECT`, за исключением того, что в предложении `SELECT` на каждой оси можно указывать только один элемент. Если на оси указано несколько элементов, возникает ошибка.  
  
 Синтаксическая конструкция `<Max_Rows>` задает максимальное количество строк в каждом возвращаемом наборе строк. Если поставщик OLE DB, используемый для соединения с источником данных, не поддерживает параметр `DBPROP_MAXROWS`, аргумент `<Max_Rows>` не учитывается.  
  
 Синтаксическая конструкция `<First_Rowset>` определяет секцию, набор строк которой возвращается первым.  
  
 Синтаксическая конструкция `<Return_Columns>` определяет возвращаемые столбцы базовой базы данных.  
  
## <a name="drillthrough-statement-example"></a>Пример инструкции DRILLTHROUGH  
 В следующем примере иллюстрируется использование инструкции `DRILLTHROUGH`. В этом примере инструкция DRILLTHROUGH обращается с запросом к концевым элементам измерений Store, Product и Time вдоль измерения Stores (ось среза) и возвращает группу мер Department, идентификатор отдела и имя сотрудника.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>См. также  
 [Манипулирование данными (многомерные выражения)](mdx-data-manipulation-manipulating-data.md)  
  
  
