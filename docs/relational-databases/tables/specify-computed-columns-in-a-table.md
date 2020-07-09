---
title: Указание вычисляемых столбцов в таблице | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, define
ms.assetid: 731a4576-09c1-47f0-a8f6-edd0b55679f4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 546490349b2d80135c873ff0917ab571f3cae830
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731584"
---
# <a name="specify-computed-columns-in-a-table"></a>Указание вычисляемых столбцов в таблице

[!INCLUDE[tsql-appliesto-ss-asdb-xxxx-xxx-md](../../includes/applies-to-version/sql-asdb.md)]

Вычисляемый столбец представляет собой виртуальный столбец, физически не хранящийся в таблице, если для него не установлен признак PERSISTED. В выражении вычисляемого столбца для вычисления значения могут использоваться данные из других столбцов. Вы можете задать выражение для вычисляемого столбца в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с использованием [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].

**В этом разделе**

- **Перед началом работы**

   [Ограничения](#Limitations)

   [Безопасность](#Security)

- **Задание вычисляемого столбца с использованием:**

   [Среда SQL Server Management Studio](#SSMSProcedure)

   [Transact-SQL](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом

### <a name="limitations-and-restrictions"></a><a name="Limitations"></a> Ограничения

- Вычисляемый столбец нельзя использовать ни в качестве определения ограничения DEFAULT или FOREIGN KEY, ни вместе с определением ограничения NOT NULL. Однако если вычисляемый столбец определен детерминированным выражением и тип данных результата допускается для индексных столбцов, то вычисляемый столбец может быть использован как ключевой столбец в индексе или как часть ограничений PRIMARY KEY или UNIQUE. Например, если таблица содержит столбцы a и b со значениями целого типа, то вычисляемый столбец a + b может быть индексирован, но вычисляемый столбец a+DATEPART(dd, GETDATE()) не может быть индексирован, так как значение может меняться при каждом следующем вычислении.
- Вычисляемый столбец не может быть целевым столбцом инструкций INSERT или UPDATE.

### <a name="security"></a><a name="Security"></a> безопасность

#### <a name="permissions"></a><a name="Permissions"></a> Permissions

Требуется разрешение ALTER на таблицу.

## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio

### <a name="to-add-a-new-computed-column"></a><a name="NewColumn"></a> Добавление нового вычисляемого столбца

1. В **обозревателе объектов**разверните таблицу, в которую нужно добавить новый вычисляемый столбец. Щелкните правой кнопкой мыши **Столбцы** и выберите **Создать столбец**.
2. Введите имя столбца и выберите тип данных по умолчанию (**nchar**(10)). Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет тип данных вычисляемого столбца путем применения правил очередности типов данных к выражениям, указанным в формуле. Например, если формула ссылается на столбец типа **money** и столбец типа **int**, то вычисляемый столбец имеет тип **money** , поскольку этот тип данных имеет более высокий приоритет. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).
3. На вкладке **Свойства столбца** раскройте свойство **Спецификация вычисляемого столбца** .
4. В дочернем свойстве **(Формула)** введите выражение для этого столбца в ячейку сетки справа. Например, в столбце `SalesTotal` можно ввести формулу `SubTotal+TaxAmt+Freight`, чтобы добавить значения в этих столбцах для каждой строки в таблице.

   > [!IMPORTANT]
   > Если формула связывает два выражения различных типов данных, то по правилам приоритета типов данных определяется, какой тип данных имеет меньший приоритет и будет преобразован в тип данных с большим приоритетом. Если неявное преобразование не поддерживается, возвращается ошибка «`Error validating the formula for column column_name.`». Используйте функцию CAST или CONVERT, чтобы устранить конфликт типа данных. Например, если столбец типа **nvarchar** объединяется со столбцом типа **int**, то целочисленный тип необходимо преобразовать в **nvarchar** , как показано в следующей формуле: `('Prod'+CONVERT(nvarchar(23),ProductID))`. Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).

5. Выберите **Да** или **Нет** в раскрывающемся списке для дочернего свойства **Материализованный** , чтобы указать, следует ли сохранять данные.

6. В меню **Файл** выберите команду **Сохранить** _имя_таблицы_.

#### <a name="to-add-a-computed-column-definition-to-an-existing-column"></a>Добавление определения вычисляемого столбца к существующему столбцу

1. В **обозревателе объектов**щелкните правой кнопкой мыши таблицу со столбцом, определение которого необходимо изменить, и разверните папку **Столбцы** .
2. Щелкните правой кнопкой мыши столбец, для которого необходимо задать формулу вычисляемого столбца, и выберите пункт **Удалить**. Нажмите кнопку **ОК**.
3. Добавьте новый столбец и укажите формулу вычисляемого столбца в соответствии с предыдущей процедурой, чтобы добавить новый вычисляемый столбец.

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-add-a-computed-column-when-creating-a-table"></a>Добавление вычисляемого столбца при создании таблицы

В следующем примере создается таблица с вычисляемым столбцом, который умножает значение столбца `QtyAvailable` на значение, указанное в столбце `UnitPrice`.

```sql
CREATE TABLE dbo.Products
   (
      ProductID int IDENTITY (1,1) NOT NULL
      , QtyAvailable smallint
      , UnitPrice money
      , InventoryValue AS QtyAvailable * UnitPrice
    )
;
-- Insert values into the table.
INSERT INTO dbo.Products (QtyAvailable, UnitPrice)
   VALUES (25, 2.00), (10, 1.5)
;
-- Display the rows in the table.
SELECT ProductID, QtyAvailable, UnitPrice, InventoryValue
FROM dbo.Products
;
```

### <a name="to-add-a-new-computed-column-to-an-existing-table"></a>Добавление нового вычисляемого столбца в существующую таблицу

В следующем примере в таблицу, созданную в предыдущем примере, будет добавлен новый столбец.

```sql
ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5)
;
```

При необходимости добавьте аргумент PERSISTED, чтобы физически хранить вычисляемые значения в таблице:

```sql
ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5) PERSISTED
;
```

### <a name="to-change-an-existing-column-to-a-computed-column"></a>Замена существующего столбца на вычисляемый столбец

В следующем примере изменяется столбец, добавленный в предыдущем примере.

```sql
ALTER TABLE dbo.Products DROP COLUMN RetailValue
;
GO
ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5)
;
```

Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).
