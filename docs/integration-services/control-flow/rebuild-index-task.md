---
description: задача «Перестроение индекса»
title: Задача "Перестроение индекса" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98be7870112403b610420a8508928ba1c60f266e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425926"
---
# <a name="rebuild-index-task"></a>задача «Перестроение индекса»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Задача «Перестроение индекса» перестраивает индекс в таблицах или представлениях базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения об управлении индексами см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 При помощи задачи «Перестроение индекса» пакет может перестроить индексы в одной или нескольких базах данных. Если задача перестраивает индексы только одной базы данных, можно выбрать представления и таблицы, индексы которых данная задача перестраивает.  
  
 Эта задача содержит инструкцию ALTER INDEX REBUILD со следующими параметрами перестроения индекса.  
  
-   Определите значение коэффициента FILLFACTOR или используйте исходное значение FILLFACTOR.  
  
-   Установите значение SORT_IN_TEMPDB = ON для сохранения промежуточных результатов сортировки, используемых для перестроения индекса в базе данных tempdb. Если этот параметр установлен в положение OFF, результат сохраняется в ту же базу данных, что и индекс.  
  
-   Установите значение PAD_INDEX = ON для выделения свободного места, которое определяется с помощью FILLFACTOR для страниц индекса промежуточного уровня.  
  
-   Установите значение IGNORE_DUP_KEY = ON, чтобы разрешить операциям многострочной вставки, которые включают в себя записи, нарушающие ограничения уникальности, вставлять те из записей, которые не нарушают этих ограничений.  
  
-   Установите значение ONLINE = ON для отмены блокировки таблицы, что позволяет производить запросы и обновления базовой таблицы во время повторного индексирования.  
  
    > [!NOTE]  
    >  Операции с индексами в сети доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
-   Укажите значение MAXDOP для ограничения числа процессоров, используемых при параллельном выполнении планов.  
  
-   Укажите WAIT_AT_LOW_PRIORITY, MAX_DURATION и ABORT_AFTER_WAIT для управления длительностью ожидания блокировок с низким приоритетом.  
  
 Дополнительные сведения об инструкции ALTER INDEX и параметрах перестроения индекса см. в разделе [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).  
  
> [!IMPORTANT]  
>  Время, необходимое задаче для создания инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , пропорционально числу индексов, которые задача перестраивает. Если задача настроена на перестроение индексов во всех таблицах и представлениях базы данных с большим числом индексов или на перестроение индексов в нескольких базах данных, ей может потребоваться существенное количество времени для формирования инструкции Transact-SQL.  
  
## <a name="configuration-of-the-rebuild-index-task"></a>Настройка задачи «Перестроение индекса»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания****области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
 [Задача "Перестроение индекса" (план обслуживания)](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
