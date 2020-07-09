---
title: MSSQLSERVER_5515 | Документация Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: a9456aed02e9e1a2566bf0281dacd07f435af44b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728372"
---
# <a name="mssqlserver_5515"></a>MSSQLSERVER_5515
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
