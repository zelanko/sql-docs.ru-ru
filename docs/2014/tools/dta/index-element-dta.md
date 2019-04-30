---
title: Индекс элемента (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Index element (DTA)
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59650edbef55b7bb433c6003c9ddc0f203ca7c5e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63229007"
---
# <a name="index-element-dta"></a>элемент Index (DTA)
  Содержит сведения об индексе, который необходимо создать в пользовательской конфигурации или удалить из нее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|Атрибут Index|Тип данных|Описание|  
|---------------------|---------------|-----------------|  
|`Clustered`|`boolean`|Необязательный. Определяет индекс как кластеризованный. Может принимать значения «true» или «false», например:<br /><br /> `<Index Clustered="true">`<br /><br /> По умолчанию этот атрибут принимает значение «false».|  
|`Unique`|`boolean`|Необязательный. Определяет индекс как уникальный. Может принимать значения «true» или «false», например:<br /><br /> `<Index Unique="true">`<br /><br /> По умолчанию этот атрибут принимает значение «false».|  
|`Online`|`boolean`|Необязательный параметр. Позволяет задать индекс, способный выполнять операции, когда сервер находится в режиме в сети, для чего требуется временное место на диске. Может принимать значения «true» или «false», например:<br /><br /> `<Index Online="true">`<br /><br /> По умолчанию этот атрибут принимает значение «false».<br /><br /> Дополнительные сведения см. в статье [Выполнение операции с индексами в сети](../../relational-databases/indexes/perform-index-operations-online.md).|  
|`IndexSizeInMB`|`double`|Необязательный параметр. Позволяет задать максимальный размер индекса в мегабайтах, например:<br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> Значения по умолчанию нет.|  
|`NumberOfRows`|`integer`|Необязательный параметр. Имитирует различные размеры индекса, что позволяет эффективно моделировать различные размеры таблиц, например:<br /><br /> `<Index NumberOfRows="3000">`<br /><br /> Значения по умолчанию нет.|  
|`QUOTED_IDENTIFIER`|`boolean`|Необязательный параметр. Заставляет [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следовать правилам ISO относительно разделения кавычками идентификаторов и строк-литералов. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в статье [SET QUOTED_IDENTIFIER (Transact-SQL)](/sql/t-sql/statements/set-quoted-identifier-transact-sql).|  
|`ARITHABORT`|`boolean`|Необязательный параметр. Завершает запрос, если во время его выполнения возникает ошибка переполнения или деления на ноль. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index ARITHABORT [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в разделе [SET ARITHABORT (Transact-SQL)](/sql/t-sql/statements/set-arithabort-transact-sql).|  
|`CONCAT_NULL_YIELDS_`<br /><br /> `NULL`|`boolean`|Необязательный параметр. Определяет, могут ли результаты объединения рассматриваться как значения NULL или пустые строковые значения. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в разделе [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).|  
|`ANSI_NULLS`|`boolean`|Необязательный параметр. Позволяет задать совместимое со стандартом ISO поведение операторов сравнения «Равно» (=) и «Не равно» (<>) при их использовании со значениями NULL. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в разделе [SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql).|  
|`ANSI_PADDING`|`boolean`|Необязательный. Управляет способом хранения в столбце значений, которые короче установленных для них размеров. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql).|  
|`ANSI_WARNINGS`|`boolean`|Необязательный. Задает поведение в соответствии со стандартом ISO для некоторых условий ошибок. Если индекс создан по вычисляемому столбцу или представлению, этот атрибут должен быть включен. Например, выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в разделе [SET ANSI_WARNINGS (Transact-SQL)](/sql/t-sql/statements/set-ansi-warnings-transact-sql).|  
|`NUMERIC_ROUNDABORT`|`boolean`|Необязательный параметр. Указывает уровень детализации отчетов об ошибках, которые формируются при потере точности во время округления. Если индекс создается по вычисляемому столбцу или представлению, этот атрибут должен быть включен.<br /><br /> Выражение со следующим синтаксисом включает этот атрибут:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> По умолчанию этот атрибут отключен.<br /><br /> Дополнительные сведения см. в статье [SET NUMERIC_ROUNDABORT (Transact-SQL)](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента `Create` или `Drop`, если не заданы никакие другие структуры физического проектирования с помощью элементов `Statistics` или `Heap`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Create (DTA)](create-element-dta.md)<br /><br /> Элемент `Drop`. Дополнительные сведения см. в разделе «XML-схема помощника по настройке ядра СУБД».|  
|**Дочерние элементы**|[Элемент Name описания индекса (DTA)](name-element-for-index-dta.md)<br /><br /> [Элемент Column описания индекса (DTA)](column-element-for-index-dta.md)<br /><br /> Элемент `PartitionScheme`. Дополнительные сведения см. в разделе «XML-схема помощника по настройке ядра СУБД».<br /><br /> Элемент `PartitionColumn`. Дополнительные сведения см. в разделе «XML-схема помощника по настройке ядра СУБД».<br /><br /> [Элемент Filegroup описания индекса (DTA)](filegroup-element-for-index-dta.md)<br /><br /> Элемент `NumberOfReferences`. Дополнительные сведения см. в разделе «XML-схема помощника по настройке ядра СУБД».<br /><br /> Элемент `PercentUsage`. Дополнительные сведения см. в разделе «XML-схема помощника по настройке ядра СУБД».|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
