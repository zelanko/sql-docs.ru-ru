---
title: MSSQLSERVER_845 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f2d9b231b6cf2152e825b07dc1e3e218815d9df1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver845"></a>MSSQLSERVER_845
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|845|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|BUFLATCH_TIMEOUT|  
|Текст сообщения|Истекло время ожидания кратковременной блокировки буфера — тип %d, страница %S_PGID, идентификатор базы данных %d.|  
  
## <a name="explanation"></a>Объяснение  
Процесс ожидал получения кратковременной блокировки, но ему не удалось получить ее до истечения времени ожидания. Это может произойти, если операциях ввода-вывода выполняется слишком долго. Обычно это происходит в результате блокировки системных процессов другими задачами. В некоторых случаях эта ошибка может возникать в результате сбоя оборудования.  
  
## <a name="user-action"></a>Действие пользователя  
Для того чтобы предотвратить эту ошибку, выполните следующие задачи:  
  
-   Уменьшите рабочую нагрузку.  
  
-   Убедитесь, что в журнале событий или журнале ошибок присутствуют взаимосвязанные сбои операций ввода-вывода. Сбои операций ввода-вывода обычно вызваны неправильной работой диска.  
  
-   Проверьте наличие невыполненных задач и других критических ошибок в журнале ошибок.  
  
-   Если критические ошибки встречаются часто, устраните их причину.  
  
Если ошибка продолжает возникать, обратитесь в службу поддержки пользователей корпорации Майкрософт.  
  
