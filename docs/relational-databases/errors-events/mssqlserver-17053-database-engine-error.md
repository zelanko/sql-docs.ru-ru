---
title: MSSQLSERVER_17053 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8fa2aabfa00f75a7abb4407dcb88cb2b75f41d69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17053|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|OS_ERROR|  
|Текст сообщения|%ls: Ошибка операционной системы %ls.|  
  
## <a name="explanation"></a>Объяснение  
Произошла общая системная ошибка.  Результирующее состояние системы неизвестно.  
  
## <a name="user-action"></a>Действие пользователя  
Обычно это сообщение выдается совместно с сообщением о другой ошибке и призвано помочь диагностировать проблему. Например, это может быть неудачная попытка чтения или записи файлов данных или журнала, операции чтения или записи в системный реестр или другие непредвиденные сбои функций Win32API.  
  
