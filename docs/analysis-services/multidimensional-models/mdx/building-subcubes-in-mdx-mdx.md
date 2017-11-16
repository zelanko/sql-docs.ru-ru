---
title: "Построение вложенных кубов в многомерных Выражениях (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9a60ea4f39735f9dfb6d8b3283faa58d38e6a075
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="building-subcubes-in-mdx-mdx"></a>Построение вложенных кубов в многомерных выражениях (многомерные выражения)
  Вложенный куб — это подмножество куба, полученное на основании отфильтрованного представления базовых данных. Ограничивая куб до вложенного куба, можно повысить производительность запросов.  
  
 Для определения вложенного куба предназначена инструкция [CREATE SUBCUBE](../../../mdx/mdx-data-definition-create-subcube.md) , описанная в данном разделе.  
  
## <a name="create-subcube-syntax"></a>Синтаксис инструкции CREATE SUBCUBE  
 Чтобы создать вложенный куб, используется следующий синтаксис:  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 Синтаксис инструкции CREATE SUBCUBE очень прост. Аргумент *Subcube_Identifier* указывает куб, из которого создается данный вложенный куб. Аргумент *Subcube_Expression* определяет часть куба, которая станет вложенным кубом.  
  
 После создания вложенного куба он становится контекстом для всех запросов многомерных выражений либо до закрытия сеанса, либо до выполнения инструкции [DROP SUBCUBE](../../../mdx/mdx-data-definition-drop-subcube.md) .  
  
### <a name="what-a-subcube-contains"></a>Содержимое вложенного куба  
 Хотя инструкция CREATE SUBCUBE довольно проста в использовании, она не указывает явно все элементы, которые войдут во вложенный куб. При определении вложенного куба применяются следующие правила.  
  
-   При включении во вложенный куб элемента иерархии **(Все)** туда включаются все элементы этой иерархии.  
  
-   При включении во вложенный куб какого-либо элемента туда включаются все его предки и потомки.  
  
-   При включении во вложенный куб всех элементов какого-либо уровня туда включаются все элементы из данной иерархии. Элементы других иерархий не включаются во вложенный куб, если они не существуют с элементами данного уровня (например, в случае несбалансированной иерархии — города, в котором нет клиентов).  
  
-   Вложенный куб всегда содержит все элементы **(Все)** из данного куба.  
  
 Кроме того, во вложенном кубе визуально подсчитываются статистические значения. Пусть вложенный куб содержит значения `USA`, `WA`и `OR`. Статистическое значение для параметра `USA` будет суммой `{WA,OR}` , поскольку `WA` и `OR` — единственные штаты, определенные во вложенном кубе. Все прочие штаты будут проигнорированы.  
  
 Кроме того, явные ссылки на ячейки вне вложенного куба возвращают значения ячеек, вычисленные в контексте всего куба. Пусть создан вложенный куб, ограниченный текущим годом. После этого можно при помощи функции [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) сравнить текущий год с предыдущим. Разность значений будет вычислена, хотя значения предыдущего года лежат вне данного вложенного куба.  
  
 Наконец, если оригинальный контекст не заменяется, функции наборов, значения которых рассчитаны в подзапросе выборки, вычисляются в контексте этого подзапроса. Если контекст заменяется, функции наборов вычисляются в контексте всего куба.  
  
## <a name="create-subcube-example"></a>Пример инструкции CREATE SUBCUBE  
 В следующем примере создается вложенный куб, ограничивающий куб «Бюджет» счетами 4200 и 4300.  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 После создания вложенного куба для сеанса, все последующие запросы будут выполняться для этого вложенного куба, а не для всего куба. Например, при выполнении следующего запроса будут возвращены только элементы счетов 4200 и 4300.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>См. также  
 [Определение контекста куба в запросе (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  

