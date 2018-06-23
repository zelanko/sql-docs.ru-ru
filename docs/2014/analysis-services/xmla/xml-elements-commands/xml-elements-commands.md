---
title: Команды (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bbfb56cc1ee12acd511c344ba3e1940fd5d56b32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097609"
---
# <a name="commands-xmla"></a>Команды (XMLA)
  Этот раздел справочника содержит элементы XML для аналитики (XMLA), которые можно использовать в элементе `Command` во время вызова метода `Execute`.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Alter (XML для аналитики)](alter-element-xmla.md)|Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../xml-elements-methods-execute.md) для изменения объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Backup, элемент](backup-element-xmla.md)|Создает резервную копию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных в файл резервной копии.|  
|[Batch, элемент](batch-element-xmla.md)|Выполняет один или несколько XML для аналитики (XMLA) команды как пакетная операция последовательно или параллельно на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[BeginTransaction, элемент](begintransaction-element-xmla.md)|Начинает транзакцию в текущем сеансе с экземпляром служб Analysis Services.|  
|[Cancel, элемент](cancel-element-xmla.md)|Отменяет команду, выполняющуюся в настоящий момент в экземпляре служб Analysis Services.|  
|[ClearCache, элемент](clearcache-element-xmla.md)|Очищает кэш памяти для указанного объекта в экземпляре служб Analysis Services.|  
|[CommitTransaction, элемент](committransaction-element-xmla.md)|Фиксирует транзакцию в текущем сеансе с экземпляром служб Analysis Services.|  
|[Create, элемент](create-element-xmla.md)|Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../xml-elements-methods-execute.md) метод для создания объектов в экземпляре служб Analysis Services.|  
|[Delete, элемент](delete-element-xmla.md)|Удаляет объект в экземпляре служб Analysis Services.|  
|[DesignAggregations, элемент](designaggregations-element-xmla.md)|Создает агрегаты для статистической схемы в экземпляре служб Analysis Services.|  
|[Drop, элемент](drop-element-xmla.md)|Удаляет элементы атрибута из измерения.|  
|[Insert, элемент](insert-element-xmla.md)|Вставляет элементы атрибута в измерение.|  
|[Lock, элемент](lock-element-xmla.md)|Блокирует указанный объект в экземпляре служб Analysis Services.|  
|[MergePartitions, элемент](mergepartitions-element-xmla.md)|Выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.|  
|[NotifyTableChange, элемент](notifytablechange-element-xmla.md)|Уведомляет экземпляр служб Analysis Services, что в таблицах указанного источника данных произошло изменение.|  
|[Process, элемент](process-element-xmla.md)|Обрабатывает объекты в экземпляре служб Analysis Services.|  
|[Restore, элемент](restore-element-xmla.md)|Восстанавливает базу данных служб Analysis Services из файла резервной копии.|  
|[RollbackTransaction, элемент](rollbacktransaction-element-xmla.md)|Выполняет откат транзакции в текущем сеансе с экземпляром служб Analysis Services.|  
|[Statement, элемент](statement-element-xmla.md)|Содержит запрос или инструкцию, отправляемых с помощью [Execute](../xml-elements-methods-execute.md) метода с экземпляром служб Analysis Services.|  
|[Subscribe, элемент](subscribe-element-xmla.md)|Подписывается на трассировку и возвращает набор строк, содержащий события трассировки для экземпляра служб Analysis Services.|  
|[Synchronize, элемент](synchronize-element-xmla.md)|Синхронизирует базу данных служб Analysis Services с другой базой данных.|  
|[Unlock, элемент](unlock-element-xmla.md)|Снимает указанную блокировку на экземпляре служб Analysis Services.|  
|[Update, элемент](../xml-elements-commands/update-element-xmla.md)|Обновляет элементы атрибута в измерении.|  
|[UpdateCells, элемент](updatecells-element-xmla.md)|Обновляет ячейки в кубе, доступном для записи.|  
  
  