---
title: COLLATIONPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06d2a9417d001e18b9bb8a5f34ce90575510e649
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944009"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Функции параметров сортировки — COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает запрошенное свойство указанных параметров сортировки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
*collation_name*  
Имена параметров сортировки. Аргумент *collation_name* имеет тип данных **nvarchar(128)** без значения по умолчанию.
  
*property*  
Свойство сортировки. Аргумент *property* имеет тип данных **varchar(128)** и может иметь любое одно из следующих значений.
  
|Имя свойства|Описание|  
|---|---|
|**CodePage**|Кодовая страница параметров сортировки не в Юникоде. Эта кодировка используется для данных типа **varchar**. Сведения о преобразовании этих значений и сопоставлении символов см. в разделах [Приложение Ж. Таблицы сопоставления DBCS и Юникода](https://msdn.microsoft.com/library/cc194886.aspx) и [Приложение З. Кодовые страницы](https://msdn.microsoft.com/library/cc195051.aspx).<br /><br />Базовый тип данных: **int**|  
|**LCID**|Код языка Windows для параметров сортировки. Это язык и региональные параметры, используемые для правил сортировки и сравнения. Сведения о преобразовании этих значений см. в статье [Структура кода языка](https://msdn.microsoft.com/library/cc233968.aspx) (сначала их необходимо преобразовать в тип **varbinary**).<br /><br />Базовый тип данных: **int**|  
|**ComparisonStyle**|Стиль сравнения Windows для параметров сортировки. Возвращает значение 0 для двоичных параметров сортировки (как (\_BIN), так и (\_BIN2)), а также если учитываются все свойства ((\_CS\_AS\_KS\_WS), (\_CS\_AS\_KS\_WS\_SC) и (\_CS\_AS\_KS\_WS\_VSS)). Значения битовой маски:<br /><br /> Игнорировать регистр: 1<br /><br /> Не учитывать диакритические знаки: 2<br /><br /> Не учитывать тип японской азбуки: 65536<br /><br /> Не учитывать ширину: 131072<br /><br /> Примечание. Хотя параметр variation-selector-sensitive (\_VSS) влияет на то, как производится сравнение, он не представлен в этом значении.<br /><br />Базовый тип данных: **int**|  
|**Версия**|Версия параметров сортировки. Возвращает значение в диапазоне от 0 до 3.<br /><br /> Параметры сортировки, имя которых содержит "140", возвращают значение 3.<br /><br /> Параметры сортировки, имя которых содержит "100", возвращают значение 2.<br /><br /> Параметры сортировки, имя которых содержит "90", возвращают значение 1.<br /><br /> Все остальные параметры сортировки возвращают 0.<br /><br />Базовый тип данных: **tinyint**|  
  
## <a name="return-types"></a>Типы возвращаемых данных
**sql_variant**
  
## <a name="examples"></a>Примеры  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>См. также раздел
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

