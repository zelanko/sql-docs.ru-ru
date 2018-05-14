---
title: MSSQLSERVER_7906 | Документация Майкрософт
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
- 7906 (Database Engine error)
ms.assetid: 9638a764-4ac1-40ae-a614-2726ebcc6ba4
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f0879067a12c4e6ff01813e43ae53957accab38
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver7906"></a>MSSQLSERVER_7906
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7906|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_FS_INVALID_TOP_LEVEL_FILE|  
|Текст сообщения|Ошибка в базе данных: файл "FILE" не является допустимым файлом Filestream.|  
  
## <a name="explanation"></a>Объяснение  
Кроме ряда специальных файлов (например, «filestream.hdr»), никакие другие файлы входить непосредственно в пространство данных FILESTREAM не должны.  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
Выполните диагностику оборудования и исправьте все найденные проблемы. Кроме того, просмотрите журнал системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал приложений, а также журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
Если неполадка не связана с оборудованием и есть безошибочная резервная копия, восстановите базу данных из этой копии.  
  
### <a name="run-dbcc-checkdb"></a>Запуск DBCC CHECKDB  
Неприменимо. Эту ошибку исправить невозможно. Если восстановить базу данных из резервной копии не удается, свяжитесь со службой поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
