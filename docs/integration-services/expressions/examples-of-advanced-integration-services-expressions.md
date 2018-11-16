---
title: Примеры расширенных выражений служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5c7a5538b4856fc64eb42acc0496690fc7733d8b
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51639528"
---
# <a name="examples-of-advanced-integration-services-expressions"></a>Примеры расширенных выражений служб Integration Services
  В этом разделе даются примеры расширенных выражений, объединяющих несколько операторов и функций. Если выражение использует управление очередностью или преобразование «Условное разбиение», результат его оценки должен быть логическим. Это ограничение, однако, не применяется к выражениям, используемым в выражениях свойств, переменных, преобразовании «Производный столбец» или в контейнере «цикл по элементам».  
  
 В следующих примерах используются базы данных **AdventureWorks** и [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В каждом примере указываются используемые в нем таблицы.  
  
## <a name="boolean-expressions"></a>Логические выражения  
  
-   В этом примере используется таблица **Product** . Выражение оценивает значение месяца в столбце **SellStartDate** и возвращает TRUE, если месяцем является любой месяц года, начиная с июня.  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   В этом примере используется таблица **Product** . Выражение оценивает округленный результат деления столбца **ListPrice** на столбец **StandardCost** и возвращает TRUE, если результат больше 1.5.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   В этом примере используется таблица **Product** . Выражение возвращает TRUE, если результатом всех трех операций является TRUE. Столбец **Size** и переменная **BikeSize** имеют несовместимые типы данных, выражение требует явного приведения, как показано во втором примере. Приведение к типу данных DT_WSTR включает в себя длину строки.  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   Этот пример использует таблицу **CurrencyRate** . Выражение сравнивает значения в таблице и значения переменных. Оно возвращает TRUE, если значения столбцов **FromCurrencyCode** или **ToCurrencyCode** равны значениям переменной и если значение **AverageRate** больше значения **EndOfDayRate**.  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   Этот пример использует таблицу **Currency** . Выражение возвращает TRUE, если первый символ в столбце **Name** — не «a» и не «A».  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     Следующее выражение дает тот же результат, но оно более эффективно, т.к. в верхний регистр переводится только одна буква.  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a>Нелогические выражения  
 Нелогические выражения используются в преобразовании «Производный столбец», в выражениях свойств и в контейнере «цикл по элементам».  
  
-   Этот пример использует таблицу **Contact** . Выражение удаляет начальные и конечные пробелы из столбцов **FirstName**, **MiddleName**и **LastName** . Оно выделяет первую букву столбца **MiddleName** , если она не NULL, сцепляет инициал второго имени и значения столбцов **FirstName** и **LastName**, а затем вставляет необходимые пробелы между значениями.  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   Этот пример использует таблицу **Contact** . Выражение проверяет значения столбца **Salutation** . Оно возвращает значение столбца **Salutation** или пустую строку.  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   В этом примере используется таблица **Product** . Выражение преобразует первую букву в столбце **Color** в верхний регистр и преобразует остальные символы в нижний регистр.  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   В этом примере используется таблица **Product** . Выражение вычисляет номер месяца, в котором был продан продукт и возвращает строку «Unknown», если столбец **SellStartDate** или столбец **SellEndDate** содержат NULL.  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   В этом примере используется таблица **Product** . Выражение вычисляет наценку на значение столбца **StandardCost** и округляет результат с точностью до двух знаков. Результат представляется в виде процентного значения.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Использование выражения в компоненте потока данных](https://msdn.microsoft.com/library/9181b998-d24a-41fb-bb3c-14eee34f910d)  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](https://go.microsoft.com/fwlink/?LinkId=746575)на сайте pragmaticworks.com  
  
  
