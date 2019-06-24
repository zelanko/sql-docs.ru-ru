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
manager: craigg
ms.openlocfilehash: 07c215c0ae360a5b386909cd64e9f3dfb2893bcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62859133"
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
  
