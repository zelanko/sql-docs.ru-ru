---
title: "COLLATIONPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f47c45f892618120b06a17f45f5d3155e092987a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Параметры сортировки функций - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает свойство указанных параметров сортировки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
*collation_name*  
Имя сортировки. *collation_name* — **nvarchar(128)**, и нет значения по умолчанию.
  
*Свойство*  
Свойство сортировки. *Свойство* — **varchar(128)**, и может принимать одно из следующих значений:
  
|Имя свойства|Description|  
|---|---|
|**CodePage**|Кодовая страница параметров сортировки не в Юникоде. См. в разделе [сопоставление таблиц в приложении G DBCS и Юникода](https://msdn.microsoft.com/en-us/library/cc194886.aspx) и [кодовых страниц в приложении H](https://msdn.microsoft.com/en-us/library/cc195051.aspx) Чтобы преобразовать эти значения и увидеть их сопоставления символов.|  
|**КОД ЯЗЫКА**|Код языка в Windows для параметров сортировки. См. в разделе [структуры LCID](https://msdn.microsoft.com/en-us/library/cc233968.aspx) для преобразования этих значений (будет необходимо преобразовать в **varbinary** первой).|  
|**ComparisonStyle**|Стиль сравнения Windows для параметров сортировки. Возвращает значение 0 для всех двоичных параметров сортировки, как (\_BIN) и (\_BIN2), а также когда чувствительны к все свойства. Значения битовой маски:<br /><br /> Не учитывать регистр: 1<br /><br /> Без учета диакритических знаков: 2<br /><br /> Не учитывать кану: 65536<br /><br /> Игнорировать ширину: 131072<br /><br /> Примечание: Даже если она влияет на способ сравнения вариантов выбора зависящие от (\_VSS) параметр не представлен в это значение.|  
|**Версия**|Версия параметров сортировки, производная от значения поля версии идентификатора параметров сортировки. Возвращает целочисленное значение от 0 до 3.<br /><br /> Параметры сортировки с «140» в имени возвращает значение 3.<br /><br /> Параметры сортировки с именем «100», возвращают значение 2.<br /><br /> Параметры сортировки с именем «90», возвращают значение 1.<br /><br /> Все остальные параметры сортировки возвращают 0.|  
  
## <a name="return-types"></a>Возвращаемые типы
**sql_variant**
  
## <a name="examples"></a>Примеры  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>См. также:
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

