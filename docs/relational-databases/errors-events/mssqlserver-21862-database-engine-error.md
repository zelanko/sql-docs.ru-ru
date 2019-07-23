---
title: MSSQLSERVER_21862 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03c0ffb40a5472de7d2fea1730eebe192430406f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056717"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|21862|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21862|  
|Текст сообщения|Столбцы FILESTREAM нельзя опубликовать в публикации с использованием метода синхронизации «database snapshot» или «database snapshot character».|  
  
## <a name="explanation"></a>Объяснение  
Данные FILESTREAM недоступны через моментальный снимок базы данных, поэтому агент моментальных снимков не сможет прочитать данные FILESTREAM, если в качестве метода синхронизации публикации указан параметр *database snapshot* или *database_snapshot_character*.  
  
## <a name="user-action"></a>Действие пользователя  
Измените метод синхронизации публикации на любой другой, кроме *database snapshot* или *database_snapshot_character*, либо просто исключите столбец FILESTREAM из публикации.  
  
