---
title: MSSQLSERVER_15404 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee32ea648fb80219052426e17e4e49d2a88dbe7a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34317825"
---
# <a name="mssqlserver15404"></a>MSSQLSERVER_15404
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|15404|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_NTGRP_ERROR|  
|Текст сообщения|Не удалось получить сведения о пользователе/группе Windows NT "*пользователь*", код ошибки *код_ошибки*.|  
  
## <a name="explanation"></a>Объяснение  
15404 используется при проверке подлинности, если указан недопустимый участник. Или олицетворение учетной записи Windows не выполняется, так как не существует связи полного уровня доверия между учетной записью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетной записью домена Windows.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что участник Windows существует и его имя указано верно.  
  
Если эта ошибка — результат отсутствия связи полного уровня доверия между учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетной записью домена Windows, то ошибку можно устранить одним из следующих способов.  
  
-   Используйте для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетную запись из домена, к которому относится пользователь Windows.  
  
-   Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует учетную запись компьютера, например Network Service или Local System, то домен, на котором находится пользователь Windows, должен доверенную связь с компьютером.  
  
-   Используйте учетную запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
