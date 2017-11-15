---
title: "MSSQLSERVER_41342 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8af7be1ae4b0a1cbba1b56bd9644d6b33cbdd8bf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
  
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
  
