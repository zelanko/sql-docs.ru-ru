---
title: TERTIARY_WEIGHTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TERTIARY_WEIGHTS_TSQL
- TERTIARY_WEIGHTS
dev_langs:
- TSQL
helpviewer_keywords:
- weights [SQL Server]
- SQL tertiary collations
- TERTIARY_WEIGHTS function
ms.assetid: 7e1f5350-260b-4c61-8c84-69bb1a214f1f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b9c1ce066768207f7a04d16e2f4c18666eb231d7
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943994"
---
# <a name="collation-functions---tertiaryweights-transact-sql"></a>Функции параметров сортировки — TERTIARY_WEIGHTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Для каждого символа в строковом выражении не в кодировке Юникода, определенном с третичными параметрами сортировки SQL, эта функция возвращает двоичную строку весовых коэффициентов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
TERTIARY_WEIGHTS( non_Unicode_character_string_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*non_Unicode_character_string_expression*  
Строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **char**, **varchar** или **varchar(max)** , определенное в третичных параметрах сортировки SQL. Список таких параметров сортировки см. в разделе «Примечания».
  
## <a name="return-types"></a>Типы возвращаемых данных
Функция `TERTIARY_WEIGHTS` возвращает значение типа **varbinary**, если *non_Unicode_character_string_expression* имеет тип **char** или **varchar**, и значение типа **varbinary(max)** , если *non_Unicode_character_string_expression* имеет тип **varchar(max)** .
  
## <a name="remarks"></a>Remarks  
Функция `TERTIARY_WEIGHTS` возвращает значение NULL, если в третичных параметрах сортировки SQL не определен аргумент *non_Unicode_character_string_expression*. В приведенной ниже таблице представлены третичные параметры сортировки SQL.
  
|Идентификатор порядка сортировки|Параметры сортировки SQL|  
|---|---|
|33|SQL_Latin1_General_Pref_CP437_CI_AS|  
|34|SQL_Latin1_General_CP437_CI_AI|  
|43|SQL_Latin1_General_Pref_CP850_CI_AS|  
|44|SQL_Latin1_General_CP850_CI_AI|  
|49|SQL_1xCompat_CP850_CI_AS|  
|53|SQL_Latin1_General_Pref_CP1_CI_AS|  
|54|SQL_Latin1_General_CP1_CI_AI|  
|56|SQL_AltDiction_Pref_CP850_CI_AS|  
|57|SQL_AltDiction_CP850_CI_AI|  
|58|SQL_Scandinavian_Pref_CP850_CI_AS|  
|82|SQL_Latin1_General_CP1250_CI_AS|  
|84|SQL_Czech_CP1250_CI_AS|  
|86|SQL_Hungarian_CP1250_CI_AS|  
|88|SQL_Polish_CP1250_CI_AS|  
|90|SQL_Romanian_CP1250_CI_AS|  
|92|SQL_Croatian_CP1250_CI_AS|  
|94|SQL_Slovak_CP1250_CI_AS|  
|96|SQL_Slovenian_CP1250_CI_AS|  
|106|SQL_Latin1_General_CP1251_CI_AS|  
|108|SQL_Ukrainian_CP1251_CI_AS|  
|113|SQL_Latin1_General_CP1253_CS_AS|  
|114|SQL_Latin1_General_CP1253_CI_AS|  
|130|SQL_Latin1_General_CP1254_CI_AS|  
|146|SQL_Latin1_General_CP1256_CI_AS|  
|154|SQL_Latin1_General_CP1257_CI_AS|  
|156|SQL_Estonian_CP1257_CI_AS|  
|158|SQL_Latvian_CP1257_CI_AS|  
|160|SQL_Lithuanian_CP1257_CI_AS|  
|183|SQL_Danish_Pref_CP1_CI_AS|  
|184|SQL_SwedishPhone_Pref_CP1_CI_AS|  
|185|SQL_SwedishStd_Pref_CP1_CI_AS|  
|186|SQL_Icelandic_Pref_CP1_CI_AS|  
  
Используйте функцию `TERTIARY_WEIGHTS` для определения вычисляемого столбца, который определяется по значениям столбца типа **char**, **varchar** или **varchar(max)** . Определение индекса для вычисляемого столбца и для столбца типа **char**, **varchar** или **varchar(max)** может повысить производительность, если столбец типа **char**, **varchar** или **varchar(max)** задан в предложении ORDER BY запроса.
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере создается вычисляемый столбец в таблице, которая применяет функцию `TERTIARY_WEIGHTS` к значениям столбца `char`.
  
```sql
CREATE TABLE TertColTable  
(Col1 char(15) COLLATE SQL_Latin1_General_Pref_CP437_CI_AS,  
Col2 AS TERTIARY_WEIGHTS(Col1));  
GO   
```  
  
## <a name="see-also"></a>См. также раздел
[Предложение ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md)
  
  
