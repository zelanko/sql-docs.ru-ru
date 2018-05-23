---
title: MSSQLSERVER_1462 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 72e7ce07964cf8d2d59f04b789ea5022d5381a50
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1462|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|Текст сообщения|Зеркальное отображение базы данных отключено вследствие ошибки в ходе операции повторного выполнения. Не удалось возобновить операцию.|  
  
## <a name="explanation"></a>Объяснение  
Операции зеркального отображения базы данных не удалось повторить запись журнала на зеркальном сервере.  
  
### <a name="possible-causes"></a>Возможные причины  
Наиболее вероятная причина заключается в том, что операция добавления файла была выполнена в основной базе данных, но завершилась неуспешно в зеркальной базе данных, так как имена файлов или структуры каталогов на основном и зеркальном серверах отличаются.  
  
## <a name="user-action"></a>Действие пользователя  
Просмотрите журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и попытайтесь найти причину этой ошибки. Попробуйте устранить причину неполадки и возобновите зеркальное отображение базы данных.  
  
## <a name="see-also"></a>См. также:  
[Устранение неполадок в конфигурации зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
