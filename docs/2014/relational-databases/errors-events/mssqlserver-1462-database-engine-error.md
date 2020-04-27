---
title: MSSQLSERVER_1462 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1a9740287c211ac6fec7414ef05dd422a28a926b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62869919"
---
# <a name="mssqlserver_1462"></a>MSSQLSERVER_1462
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
 [Диагностика конфигурации зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
