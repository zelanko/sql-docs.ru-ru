---
title: "Примеры расширенных выражений служб Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "функции [службы Integration Services]"
  - "операторы [службы Integration Services]"
  - "выражения [службы Integration Services], примеры"
  - "примеры [службы Integration Services]"
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# Примеры расширенных выражений служб Integration Services
  В этом разделе даются примеры расширенных выражений, объединяющих несколько операторов и функций. Если выражение использует управление очередностью или преобразование «Условное разбиение», результат его оценки должен быть логическим. Это ограничение, однако, не применяется к выражениям, используемым в выражениях свойств, переменных, преобразовании «Производный столбец» или в контейнере «цикл по элементам».  
  
 В следующих примерах используются базы данных **AdventureWorks** и [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В каждом примере указываются используемые в нем таблицы.  
  
## Логические выражения  
  
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
  
## Нелогические выражения  
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
  
## Связанные задачи  
 [Использование выражения в компоненте потока данных](../Topic/Use%20an%20Expression%20in%20a%20Data%20Flow%20Component.md)  
  
## См. также  
 Техническая статья [Памятка выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=746575)на сайте pragmaticworks.com  
  
  