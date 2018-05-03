---
title: COLLATIONPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 041b1bdcc190980d471b48e7525da0fa035d087a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Функции параметров сортировки — COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает свойство указанных параметров сортировки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
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
  
|Имя свойства|Description|  
|---|---|
|**CodePage**|Кодовая страница параметров сортировки не в Юникоде. Сведения о преобразовании этих значений и сопоставлении символов см. в разделах [Приложение Ж. Таблицы сопоставления DBCS и Юникода](https://msdn.microsoft.com/en-us/library/cc194886.aspx) и [Приложение З. Кодовые страницы](https://msdn.microsoft.com/en-us/library/cc195051.aspx).|  
|**LCID**|Код языка в Windows для параметров сортировки. Сведения о преобразовании этих значений см. в статье [Структура кода языка](https://msdn.microsoft.com/en-us/library/cc233968.aspx) (сначала их необходимо преобразовать в тип **varbinary**).|  
|**ComparisonStyle**|Стиль сравнения Windows для параметров сортировки. Возвращает значение 0 для всех двоичных параметров сортировки (как (\_BIN), так и (\_BIN2)), а также если все свойства учитывают регистр. Значения битовой маски:<br /><br /> Не учитывать регистр: 1<br /><br /> Не учитывать диакритические знаки: 2<br /><br /> Не учитывать тип японской азбуки: 65536<br /><br /> Не учитывать ширину: 131072<br /><br /> Примечание. Хотя параметр variation-selector-sensitive (\_VSS) влияет на то, как производится сравнение, он не представлен в этом значении.|  
|**Версия**|Версия параметров сортировки, производная от значения поля версии идентификатора параметров сортировки. Возвращает целое число от 0 до 3.<br /><br /> Параметры сортировки, имя которых содержит "140", возвращают значение 3.<br /><br /> Параметры сортировки, имя которых содержит "100", возвращают значение 2.<br /><br /> Параметры сортировки, имя которых содержит "90", возвращают значение 1.<br /><br /> Все остальные параметры сортировки возвращают 0.|  
  
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
  
  

