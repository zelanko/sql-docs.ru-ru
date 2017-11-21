---
title: "MSSQLSERVER_825 | Документация Майкрософт"
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
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6cf3cceebd5555e91d3753e385d28164680241f5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver825"></a>MSSQLSERVER_825
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|825|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|B_RETRYWORKED|  
|Текст сообщения|Успешное чтение файла "%ls" при смещении %#016I64x после %d неудачных попыток с ошибкой: %ls. Дополнительные сведения см. в журнале ошибок SQL Server и журнале системных событий. Данное ошибочное условие может нарушить целостность базы данных и должно быть исправлено. Выполните полную проверку базы данных на согласованность (DBCC CHECKD). Эта ошибка может быть вызвана многими причинами. Дополнительные сведения см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает, что операцию чтения пришлось повторить, по меньшей мере, один раз, что свидетельствует о серьезной проблеме с оборудованием жесткого диска. В настоящее время данное сообщение не указывает на проблему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но если не исправить ошибку диска вовремя, то она может привести к потере данных или повреждению базы данных. В журнале системных событий могут содержаться связанные события, способствующие диагностированию проблемы. Дополнительные сведения об ошибках ввода-вывода см. в [главе 2 документации Майкрософт об основных операциях ввода-вывода в SQL Server](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Действие пользователя  
Следующие действия помогут идентифицировать и исправить основную проблему.  
  
-   Просмотрите журнал ошибок и переменный текст данного сообщения, объясняющие суть проблемы.  
  
-   Проверьте дисковую систему. Проблема может быть связана с жесткими дисками, контроллерами дисков, контроллерами дисковых массивов или драйверами дисков.  
  
-   Обратитесь к производителю диска за новейшими утилитами проверки состояния дисковой системы.  
  
-   Обратитесь к производителю диска за новейшими обновлениями драйверов.  
  

