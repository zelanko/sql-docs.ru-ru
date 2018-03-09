---
title: "MSSQLSERVER_41342 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d3dc1d6bff5855b5aff6bbd36d08bcde3ccc828
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
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
  
