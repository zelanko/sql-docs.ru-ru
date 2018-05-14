---
title: MSSQLSERVER_5515 | Документация Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: f3da12118485c8aa64a493529914cd83094695b9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver5515"></a>MSSQLSERVER_5515
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|5515|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FS_OPEN_CONTAINER_FAILED|  
|Текст сообщения|Не удалось открыть каталог-контейнер «%.*ls» файла FILESTREAM. Операционная система возвратила код состояния Windows 0x%x.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось открыть указанный каталог-контейнер для файла FILESTREAM.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы выяснить причину ошибки, см. конкретный код состояния Windows.  
  
