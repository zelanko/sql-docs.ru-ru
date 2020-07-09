---
title: Категория событий Performance | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5c9db194a87092fb9d24ed9ae1c1bb80e664af40
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85791029"
---
# <a name="performance-event-category"></a>Категория событий Performance
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  Категория событий **Performance** используется для контроля классов событий **Showplan** и классов событий, формируемых при выполнении операторов SQL языка DML.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md)|Указывает, что произошло автоматическое обновление статистики индекса и столбца.|  
|[Класс событий Degree of Parallelism (7.0 Insert)](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции SELECT, INSERT, UPDATE или DELETE были выполнены с использованием последовательного или параллельного плана. В отчет также включается количество ЦП, использованных для выполнения операции.|  
|[Класс событий Performance Statistics](../../relational-databases/event-classes/performance-statistics-event-class.md)|Наблюдает за производительностью выполняемых запросов.|  
|[Класс событий Showplan All](../../relational-databases/event-classes/showplan-all-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL.|  
|[Класс событий Showplan All for Query Compile](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** .|  
|[Класс событий Showplan Statistics Profile](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)|Отображает предполагаемую стоимость запроса.|  
|[Класс событий Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL. Класс событий хранит описание каждого события как правильный XML-документ.|  
|[Класс событий Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** в формате XML.|  
|[Класс событий Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)|Идентифицирует операторы **Showplan** , связанные с инструкцией SQL. Выходом является XML-документ.|  
|[Класс событий SQL:FullTextQuery](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|Указывает на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершил выполнение полнотекстового запроса.|  
|[Класс событий Plan Guide Successful](../../relational-databases/event-classes/plan-guide-successful-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешно создан план выполнения для запроса или пакета, в котором содержится структура плана.|  
|[Класс событий Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md)|Указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать план выполнения для запроса или пакета, в котором содержится структура плана.|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
