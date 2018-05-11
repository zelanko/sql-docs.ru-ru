---
title: MSSQLSERVER_41342 | Документация Майкрософт
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
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6b9ee43a6cc137e44e4c772001be7b8640181dd6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41342|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_HW_NOT_SUPPORTED|  
|Текст сообщения|Модель процессора в системе не поддерживает создание *конструкция*. Эта ошибка обычно возникает со старыми процессорами. Дополнительные сведения о поддерживаемых моделях см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="explanation"></a>Объяснение  
Для оптимизированных для памяти таблиц требуется модель процессора, которая поддерживает операции сравнения и обмена с 128-разрядными значениями, для чего требуется инструкция сборки CMPXCHG16B. Некоторые старые модели процессоров AMD не поддерживают инструкцию CMPXCHG16B. Кроме того, некоторые среды виртуализации не включают эту инструкцию по умолчанию.  
  
## <a name="user-action"></a>Действие пользователя  
Обновите процессор. Если процессор поддерживает инструкцию и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется в виртуальной машине, измените конфигурацию для поддержки инструкции CMPXCHG16B.  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
