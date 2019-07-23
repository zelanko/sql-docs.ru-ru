---
title: Автоматическое соединение самосоединения (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 66ba00a9ec4a8d39afd805c0dca45dbc70e4932e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264323"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Автоматическое создание самосоединения (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Если таблица имеет рефлексивную связь в базе данных, можно автоматически создать самосоединение.  
  
### <a name="to-create-a-self-join-automatically"></a>Автоматическое создание самосоединения  
  
1.  Добавьте на [панель диаграмм](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) нужную таблицу.  
  
2.  Еще раз добавьте эту таблицу, чтобы на панели диаграмм эта таблица была показана дважды.  
  
    [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) присваивает второму экземпляру псевдоним, добавляя порядковый номер к имени таблицы. Кроме того, конструктор запросов и представлений создает линию соединения между двумя прямоугольниками, представляющими два разных способа, которыми таблица участвует в запросе.  
  
## <a name="see-also"></a>См. также:  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
