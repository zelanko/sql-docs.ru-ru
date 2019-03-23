---
title: Задача "Перестроение индекса" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9e89c081c1c543c198a827955ab4865709ead391
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58392692"
---
# <a name="rebuild-index-task"></a>задача «Перестроение индекса»
  Задача «Перестроение индекса» перестраивает индекс в таблицах или представлениях базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения об управлении индексами см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 При помощи задачи «Перестроение индекса» пакет может перестроить индексы в одной или нескольких базах данных. Если задача перестраивает индексы только одной базы данных, можно выбрать представления и таблицы, индексы которых данная задача перестраивает.  
  
 Эта задача содержит инструкцию ALTER INDEX REBUILD со следующими параметрами перестроения индекса.  
  
-   Определите значение коэффициента FILLFACTOR или используйте исходное значение FILLFACTOR.  
  
-   Установите значение PAD_INDEX = ON для выделения свободного места, которое определяется с помощью FILLFACTOR для страниц индекса промежуточного уровня.  
  
-   Установите значение SORT_IN_TEMPDB = ON для сохранения промежуточных результатов сортировки, используемых для перестроения индекса в базе данных tempdb. Если этот параметр установлен в положение OFF, результат сохраняется в ту же базу данных, что и индекс.  
  
-   Установите значение IGNORE_DUP_KEY = ON, чтобы разрешить операциям многострочной вставки, которые включают в себя записи, нарушающие ограничения уникальности, вставлять те из записей, которые не нарушают этих ограничений.  
  
-   Установите значение ONLINE = ON для отмены блокировки таблицы, что позволяет производить запросы и обновления базовой таблицы во время повторного индексирования.  
  
> [!NOTE]  
>  Операции с индексами в режиме "в сети" доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Дополнительные сведения об инструкции ALTER INDEX и параметрах перестроения индекса см. в разделе [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Время, необходимое задаче для создания инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , пропорционально числу индексов, которые задача перестраивает. Если задача настроена на перестроение индексов во всех таблицах и представлениях базы данных с большим числом индексов или на перестроение индексов в нескольких базах данных, ей может потребоваться существенное количество времени для формирования инструкции Transact-SQL.  
  
## <a name="configuration-of-the-rebuild-index-task"></a>Настройка задачи «Перестроение индекса»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующем разделе:  
  
 [Задача "Перестроение индекса" (план обслуживания)](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
