---
title: MSSQLSERVER_7904 | Документация Майкрософт
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
- 7904 (Database Engine error)
ms.assetid: d047920c-f864-4338-b15f-49820886fbc5
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da5927fd791edaf083128e7a3f49de71269925d7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver7904"></a>MSSQLSERVER_7904
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7904|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_FS_MISSING_FILE|  
|Текст сообщения|Ошибка в таблице: не найден файл FILESTREAM для столбца с идентификатором C_ID, ROWGUID RG_ID в объекте с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID.|  
  
## <a name="explanation"></a>Объяснение  
Значение столбца секции не содержит нужного файла FILESTREAM в соответствующем каталоге столбца FILESTREAM.  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
Выполните диагностику оборудования и исправьте все найденные проблемы. Кроме того, просмотрите журнал системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал приложений, а также журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
Если неполадка не связана с оборудованием и есть безошибочная резервная копия, восстановите базу данных из этой копии.  
  
### <a name="run-dbcc-checkdb"></a>Запуск DBCC CHECKDB  
Неприменимо. Эту ошибку исправить невозможно. Если восстановить базу данных из резервной копии не удается, свяжитесь со службой поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
