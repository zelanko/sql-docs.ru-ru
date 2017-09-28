---
title: "COLLATIONPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94cbf96a25a84af1eddce9d94555be9c558c3470
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="collation-functions---collationproperty-transact-sql"></a>Параметры сортировки функций - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
|**CodePage**|Кодовая страница параметров сортировки не в Юникоде.|  
|**КОД ЯЗЫКА**|Код языка в Windows для параметров сортировки.|  
|**ComparisonStyle**|Стиль сравнения Windows для параметров сортировки. Возвращает значение 0 для всех двоичных параметров сортировки.|  
|**Версия**|Версия параметров сортировки, производная от значения поля версии идентификатора параметров сортировки. Возвращает значение 2, 1 или 0.<br /><br /> Параметры сортировки с именем «100»), возвращают значение 2.<br /><br /> Сортировки, имя которых содержит «90», возвращают значение 1.<br /><br /> Все остальные параметры сортировки возвращают 0.|  
  
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
  
  


