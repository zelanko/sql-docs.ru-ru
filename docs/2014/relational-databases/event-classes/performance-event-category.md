---
title: Категория событий Performance | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85052813"
---
# <a name="performance-event-category"></a>Категория событий Performance
  Категория событий **Performance** используется для контроля классов событий **Showplan** и классов событий, формируемых при выполнении операторов SQL языка DML.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Auto Stats](auto-stats-event-class.md)|Указывает, что произошло автоматическое обновление статистики индекса и столбца.|  
|[Класс событий Degree of Parallelism (7.0 Insert)](degree-of-parallelism-7-0-insert-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции SELECT, INSERT, UPDATE или DELETE были выполнены с использованием последовательного или параллельного плана. В отчет также включается количество ЦП, использованных для выполнения операции.|  
|[Класс событий Performance Statistics](performance-statistics-event-class.md)|Наблюдает за производительностью выполняемых запросов.|  
|[Класс событий Showplan All](showplan-all-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL.|  
|[Класс событий Showplan All for Query Compile](showplan-all-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** .|  
|[Класс событий Showplan Statistics Profile](showplan-statistics-profile-event-class.md)|Отображает предполагаемую стоимость запроса.|  
|[Класс событий Showplan XML](showplan-xml-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL. Класс событий хранит описание каждого события как правильный XML-документ.|  
|[Класс событий Showplan XML for Query Compile](showplan-xml-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** в формате XML.|  
|[Класс событий Showplan XML Statistics Profile](showplan-xml-statistics-profile-event-class.md)|Идентифицирует операторы **Showplan** , связанные с инструкцией SQL. Выходом является XML-документ.|  
|[Класс событий SQL:FullTextQuery](sql-fulltextquery-event-class.md)|Указывает на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершил выполнение полнотекстового запроса.|  
|[Класс событий Plan Guide Successful](plan-guide-successful-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешно создан план выполнения для запроса или пакета, в котором содержится структура плана.|  
|[Класс событий Plan Guide Unsuccessful](plan-guide-unsuccessful-event-class.md)|Указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать план выполнения для запроса или пакета, в котором содержится структура плана.|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../extended-events/extended-events.md)  
  
  
