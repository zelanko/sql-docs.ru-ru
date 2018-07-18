---
title: Задача "Перестроение индекса" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 528be12077056a250277f3497798d5f1f09fc3f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149645"
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
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
