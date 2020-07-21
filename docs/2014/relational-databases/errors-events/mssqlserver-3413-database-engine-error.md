---
title: MSSQLSERVER_3413 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbe1b0d69fa07875c987ccc7f7ad51b40a5f7fc4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551592"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3413|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MARKDB|  
|Текст сообщения|Идентификатор базы данных %d. Не удалось пометить базу данных как подозрительную. Не удалось выполнить просмотр Getnext NC по sys.databases.database_id. Просмотрите предыдущие ошибки в журнале ошибок для определения причины и устраните выявленные проблемы.|  
  
## <a name="explanation"></a>Объяснение  
 При попытке пометить в каталоге пользовательскую базу данных признаком SUSPECT произошел непредвиденный сбой. Состояние SUSPECT установлено не будет.  
  
## <a name="user-action"></a>Действие пользователя  
 Для исправления этой неполадки см. предыдущие ошибки.  
  
  
