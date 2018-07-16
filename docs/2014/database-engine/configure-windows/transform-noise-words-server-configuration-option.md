---
title: Параметр конфигурации сервера "transform noise words" | Документы Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
caps.latest.revision: 43
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 708333809439bcada782b72ce67890dc7b3d5799
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231944"
---
# <a name="transform-noise-words-server-configuration-option"></a>Параметр конфигурации сервера «transform noise words»
  Используйте `transform noise words` параметр конфигурации сервера, чтобы подавить сообщение об ошибке если неучитываемые слова, то есть [стоп-слов](../../relational-databases/search/full-text-search.md), логическая операция на полнотекстовый запрос возвращает 0 строк. Этот параметр удобно использовать в полнотекстовых запросах с предикатом CONTAINS, в котором логические операции или операции NEAR содержат пропускаемые слова. Возможные значения описаны в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Пропускаемые слова (или стоп-слова) не преобразуются. Если полнотекстовый запрос содержит стоп-слова, то запрос возвращает 0 строк, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает предупреждение. Это поведение по умолчанию.<br /><br /> Обратите внимание на то, что это предупреждение относится во время выполнения. поэтому, если полнотекстовое предложение в запросе не выполняется, предупреждение не выдается. Для локального запроса предупреждение возвращается только при наличии в нем нескольких полнотекстовых предложений. Для удаленного запроса связанный сервер может не передать ошибку, поэтому сообщение может не отобразиться.|  
|1|Пропускаемые слова (или стоп-слова) преобразуются. Они пропускаются, а остальная часть запроса обрабатывается.<br /><br /> Если пропускаемые слова встречаются в предложениях, обозначающих расстояние, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет их. Например, пропускаемое слово `is` удаляется из фразы `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, в результате чего поисковый запрос преобразуется в `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`. Обратите внимание, что запрос `CONTAINS(<column_name>, 'NEAR(hello,is)')` будет преобразован просто в `CONTAINS(<column_name>, hello)` , поскольку там всего одно допустимое слово поиска.|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a>Действие настройки transform noise words  
 В этом разделе проиллюстрировано поведение запросов с пропускаемым словом "`the`«, в другой настройке параметра `transform noise words`.  Предполагается обработка образцов строк полнотекстовых запросов по строке таблицы со следующими данными: `[1, "The black cat"]`.  
  
> [!NOTE]  
>  Все подобные сценарии могут выдавать предупреждение о пропускаемых словах.  
  
-   Если значение параметра transform noise words — 0:  
  
    |Строка запроса|Результат|  
    |------------------|------------|  
    |«`cat`» AND «`the`»|Нет результатов (поведение аналогично «"`the`" AND "`cat`"».)|  
    |«`cat`» NEAR «`the`»|Нет результатов (поведение аналогично «"`the`" NEAR "`cat`"».)|  
    |«`the`» AND NOT «`black`»|Нет результатов|  
    |«`black`» AND NOT «`the`»|Нет результатов|  
  
-   Если значение параметра transform noise words — 1:  
  
    |Строка запроса|Результат|  
    |------------------|------------|  
    |«`cat`» AND «`the`»|Попадание для строки с идентификатором 1|  
    |«`cat`» NEAR «`the`»|Попадание для строки с идентификатором 1|  
    |«`the`» AND NOT «`black`»|Нет результатов|  
    |«`black`» AND NOT «`the`»|Попадание для строки с идентификатором 1|  
  
## <a name="example"></a>Пример  
 В данном примере параметр `transform noise words` имеет значение `1`.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql)  
  
  
