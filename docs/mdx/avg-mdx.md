---
title: AVG (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aa8817e35a589def4631bd455637d05fc62d3a0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017014"
---
# <a name="avg-mdx"></a>Avg (многомерные выражения)


  Вычисляет набор и возвращает среднее непустых значений ячеек набора; среднее считается по мерам в наборе или по указанной мере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Avg( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Если задан набор пустых кортежей или пустой набор, функция **AVG** возвращает пустое значение.  
  
 Функция **AVG** вычисляет среднее для непустых значений ячеек в заданном наборе, сначала вычисляя сумму значений по ячейкам в указанном наборе, а затем вычисляет вычисленную сумму по количеству непустых ячеек в указанном наборе.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] отбрасывает неопределенные значения при вычислении среднего значения для набора чисел.  
  
 Если определенное числовое выражение (обычно мера) не указано, функция **AVG** усредняет среднюю величину в текущем контексте запроса. Если указана определенная мера, функция **AVG** сначала вычисляет меру по набору, а затем функция вычисляет среднее на основе указанной меры.  
  
> [!NOTE]  
>  При использовании функции **CurrentMember** в операторе вычисляемого элемента необходимо указать числовое выражение, так как для текущей координаты в таком контексте запроса не существует меры по умолчанию.  
  
 Чтобы принудительно включить пустые ячейки, приложение должно использовать функцию [CoalesceEmpty](../mdx/coalesceempty-mdx.md) или указать допустимое *Numeric_Expression* , предоставляющее нулевое значение (0) для пустых значений. Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает среднее значение для меры в указанном наборе.  Обратите внимание, что заданная мера может быть либо мерой по умолчанию для элементов указанного набора, либо указанной мерой.  
  
 `WITH SET [NW Region] AS`  
  
 `{[Geography].[State-Province].[Washington]`  
  
 `, [Geography].[State-Province].[Oregon]`  
  
 `, [Geography].[State-Province].[Idaho]}`  
  
 `MEMBER [Geography].[Geography].[NW Region Avg] AS`  
  
 `AVG ([NW Region]`  
  
 `--Uncomment the line below to get an average by Reseller Gross Profit Margin`  
  
 `--otherwise the average will be by whatever the default measure is in the cube,`  
  
 `--or whatever measure is specified in the query`  
  
 `--, [Measures].[Reseller Gross Profit Margin]`  
  
 `)`  
  
 `SELECT [Date].[Calendar Year].[Calendar Year].Members ON 0`  
  
 `FROM [Adventure Works]`  
  
 `WHERE ([Geography].[Geography].[NW Region Avg])`  
  
 В следующем примере возвращается ежедневное среднее значение `Measures.[Gross Profit Margin]` меры, вычисленное по дням каждого месяца в 2003 финансовом году из куба **Adventure Works** . Функция **AVG** вычисляет среднее значение из набора дней, содержащихся в каждом месяце `[Ship Date].[Fiscal Time]` иерархии. Первая версия вычислений показывает поведение функции Avg по умолчанию, состоящее в исключении из среднего значения дней, в которые не было зафиксировано ни одной продажи. Вторая версия показывает, как включить в среднее значение дни без продаж.  
  
 `WITH MEMBER Measures.[Avg Gross Profit Margin] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `Measures.[Gross Profit Margin]`  
  
 `), format_String='percent'`  
  
 `MEMBER Measures.[Avg Gross Profit Margin Including Empty Days] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `CoalesceEmpty(Measures.[Gross Profit Margin],0)`  
  
 `), Format_String='percent'`  
  
 `SELECT`  
  
 `{Measures.[Avg Gross Profit Margin],Measures.[Avg Gross Profit Margin Including Empty Days]} ON COLUMNS,`  
  
 `[Ship Date].[Fiscal].[Fiscal Year].Members ON ROWS`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Product].&[344])`  
  
 В следующем примере возвращается ежедневное среднее значение `Measures.[Gross Profit Margin]` меры, вычисленное по дням каждого полугодия в 2003 финансового года из куба **Adventure Works** .  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS  
   Avg(  
      Descendants(  
         [Ship Date].[Fiscal].CurrentMember,   
            [Ship Date].[Fiscal].[Date]  
      ),   
      Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
      [Ship Date].[Fiscal].[Fiscal Year].[FY 2003].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
