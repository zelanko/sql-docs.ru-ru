---
title: "Параметр конфигурации сервера \"transform noise words\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
caps.latest.revision: "43"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1993c216407c262d9256da15ecf81a2854c2b840
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="transform-noise-words-server-configuration-option"></a>Параметр конфигурации сервера «transform noise words»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  С помощью параметра конфигурации сервера **transform noise words** отключите сообщения об ошибках, если из-за пропускаемых слов (т. е. [стоп-слов](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) логическая операция в полнотекстовом запросе возвращает 0 строк. Этот параметр удобно использовать в полнотекстовых запросах с предикатом CONTAINS, в котором логические операции или операции NEAR содержат пропускаемые слова. Возможные значения описаны в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Пропускаемые слова (или стоп-слова) не преобразуются. Если полнотекстовый запрос содержит стоп-слова, то запрос возвращает 0 строк, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает предупреждение. Это поведение по умолчанию.<br /><br /> Примечание. Это предупреждение относится ко времени выполнения, поэтому, если полнотекстовое предложение в запросе не выполняется, предупреждение не выдается. Для локального запроса предупреждение возвращается только при наличии в нем нескольких полнотекстовых предложений. Для удаленного запроса связанный сервер может не передать ошибку, поэтому сообщение может не отобразиться.|  
|1|Пропускаемые слова (или стоп-слова) преобразуются. Они пропускаются, а остальная часть запроса обрабатывается.<br /><br /> Если пропускаемые слова встречаются в предложениях, обозначающих расстояние, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет их. Например, пропускаемое слово `is` удаляется из фразы `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, в результате чего поисковый запрос преобразуется в `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`. Обратите внимание, что запрос `CONTAINS(<column_name>, 'NEAR(hello,is)')` будет преобразован просто в `CONTAINS(<column_name>, hello)` , поскольку там всего одно допустимое слово поиска.|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a>Действие настройки transform noise words  
 В этом разделе проиллюстрировано поведение запросов с пропускаемым словом "`the`" при другой настройке параметра **transform noise words**.  Предполагается обработка образцов строк полнотекстовых запросов по строке таблицы со следующими данными: `[1, "The black cat"]`.  
  
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
 В следующем примере параметр **transform noise words** имеет значение `1`.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)  
  
  
