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
ms.openlocfilehash: 5d9eb240ffe26a91b59413468f54cf5b2376779e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780925"
---
# <a name="mssqlserver_17053"></a>MSSQLSERVER_17053
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
