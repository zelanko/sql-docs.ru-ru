---
description: MSSQLSERVER_5515
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
ms.openlocfilehash: aecbc4ad6ee5c3f8a0ebcf596dca0a06392acedf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470915"
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
  
