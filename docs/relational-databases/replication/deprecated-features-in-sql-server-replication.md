---
description: Устаревшие функции репликации SQL Server
title: Устаревшие функции репликации в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/22/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [SQL Server replication]
ms.assetid: 46bd3edd-d6de-40a6-a015-21cce8321feb
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 3a81ec710ed3d0927d7839309de371066ff81445
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461875"
---
# <a name="deprecated-features-in-sql-server-replication"></a>Устаревшие функции репликации SQL Server
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  В этом разделе описаны устаревшие компоненты репликации, по-прежнему доступные в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="items-deprecated-in-sssql15"></a>Элементы, нерекомендуемые в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
|Компонент|Описание|  
|-------------|-----------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Репликация поддерживается, если на каждой конечной точке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлена одна из двух основных версий текущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] не поддерживает репликацию в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]либо оттуда.|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)]|Репликация поддерживается, если на каждой конечной точке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлена одна из двух основных версий текущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] не поддерживает репликацию в тип данных [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Обратная совместимость репликации](../../relational-databases/replication/replication-backward-compatibility.md)  
  
  
