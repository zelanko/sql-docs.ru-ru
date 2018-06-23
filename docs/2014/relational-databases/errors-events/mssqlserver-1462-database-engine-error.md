---
title: MSSQLSERVER_1462 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e1de41c30aae242bdb5fae3524b06e98bad21863
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100635"
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
    
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
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок в конфигурации зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  