---
title: MSSQLSERVER_17883 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f9f712ed8d37872c90eff773e81a657fb96c296
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213174"
---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17883|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_SCHEDULER_NONYIELDING|  
|Текст сообщения|Процесс %ld:%ld:%ld (0x%lx) Worker 0x%p, по-видимому, не возвращает управление планировщику %ld. Время создания потока: %I64d. Примерная загрузка ЦП для потока: ядро %I64d мс, пользователь %I64d мс. Эффективность использования процесса %d%%. Бездействие системы %d%%. Интервал: %I64d мс.|  
  
## <a name="explanation"></a>Объяснение  
 Указывает на возможную проблему, в результате которой поток не возвращает управление планировщику.  Возможно, это сбой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не получает достаточно циклов процессора для выполнения.  Эта ошибка может исчезнуть, если поток, в конце концов, передаст управление.  
  
## <a name="user-action"></a>Действие пользователя  
 В случае избыточной нагрузки на систему уменьшите ее. В противном случае обратитесь в службу поддержки пользователей Майкрософт.  
  
  
