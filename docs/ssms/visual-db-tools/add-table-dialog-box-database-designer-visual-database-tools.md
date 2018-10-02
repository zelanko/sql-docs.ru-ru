---
title: Диалоговое окно "Добавление таблицы" в конструкторе базы данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ca667e010b150137f9a50ca1ed61ff0f233fba2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793052"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Диалоговое окно «Добавление таблицы» (конструктор базы данных) (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Позволяет добавлять таблицы в конструкторе базы данных.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
**Обновить**  
Обновляет список таблиц для соответствия текущему состоянию базы данных.  
  
**Добавить**  
Добавляет выбранную таблицу или таблицы.  
  
> [!NOTE]  
> Если нужно добавить несколько таблиц к диаграмме, можно выбрать их все, а затем нажать кнопку **Добавить**. Или можно дважды щелкнуть каждую таблицу, которую нужно добавить, а затем, по окончании, нажать кнопку **Закрыть** .  
  
**Закрыть**  
Закрывает диалоговое окно без дальнейшего добавления таблиц.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в диаграммы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
