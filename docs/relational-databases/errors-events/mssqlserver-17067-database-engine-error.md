---
title: MSSQLSERVER_17067 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17067 (Database Engine error)
ms.assetid: 32c1f0e8-db70-4836-95b2-8833be9e0ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6df9cdae6fc21d073dfc69f392232a20ca2d0377
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68100385"
---
# <a name="mssqlserver_17067"></a>MSSQLSERVER_17067
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17067|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLASSERT_MESG|  
|Текст сообщения|Проверочное утверждение SQL Server: файл: \<%s>, строка = %d %s. Возможно, эта ошибка связана со временем. Если ошибка не исчезнет после повторного выполнения инструкции, проверьте целостность структуры базы данных при помощи инструкции DBCC CHECKDB или перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка может быть вызвана нерегулярными проблемами, связанными со временем, или повреждением данных в памяти или на диске.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните повторно инструкцию, которая вызвала появление исключения. Если ошибка вызвана событием, связанным со временем, она, возможно, не повторится. Если ошибка не исчезла, проверьте диск на наличие повреждений при помощи инструкции DBCC CHECKDB. Перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.  
  
## <a name="see-also"></a>См. также:  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
