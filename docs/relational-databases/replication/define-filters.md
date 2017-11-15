---
title: "Определение фильтров | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords: Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce7cc0ad6f84172f74a11be2d519c7804d35f484
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="define-filters"></a>Определение фильтров
  Диалоговое окно **Определение фильтров** позволяет определять фильтры, применяемые к конфликтам данных для просмотра подмножества этих конфликтов в данной сетке. Чтобы определить фильтр, выберите оператор из раскрывающегося списка **Оператор** , а затем введите значение. Например, чтобы просмотреть только те конфликты, в которых проигравшей стороной является сервер **ReplTest1**, выберите **Равно** из раскрывающегося списка **Оператор** и введите **ReplTest1** в первом столбце **Значение** .  
  
## <a name="options"></a>Параметры  
 **Оператор**  
 Выберите оператор для фильтра, например **Меньше**или Равно.  
  
 **Значение**  
 Введите значение для фильтра. Для большинства операторов нужно только значение в первом столбце **Значение** , но для операторов **Между** и **Вне** необходимы значения в обоих столбцах **Значение** .  
  
 **Clear**  
 Нажмите эту кнопку для сброса всех ранее определенных фильтров.  
  
## <a name="see-also"></a>См. также:  
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация слиянием)](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация транзакций)](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
