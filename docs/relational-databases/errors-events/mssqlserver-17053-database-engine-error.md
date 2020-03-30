---
title: MSSQLSERVER_17053 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d078557186af534f1f489e8fee2e0f803c548f58
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68100434"
---
# <a name="mssqlserver_17053"></a>MSSQLSERVER_17053
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17053|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|OS_ERROR|  
|Текст сообщения|%ls: Ошибка операционной системы %ls.|  
  
## <a name="explanation"></a>Объяснение  
Произошла общая системная ошибка.  Результирующее состояние системы неизвестно.  
  
## <a name="user-action"></a>Действие пользователя  
Обычно это сообщение выдается совместно с сообщением о другой ошибке и призвано помочь диагностировать проблему. Например, это может быть неудачная попытка чтения или записи файлов данных или журнала, операции чтения или записи в системный реестр или другие непредвиденные сбои функций Win32API.  
  
