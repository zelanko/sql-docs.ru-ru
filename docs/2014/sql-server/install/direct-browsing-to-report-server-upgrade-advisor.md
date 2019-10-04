---
title: Прямой просмотр сервера отчетов (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 6945828b2eba829c32d717c13393c9fbda4fc43e
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952209"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Прямой переход на сервер отчетов (советник по переходу)
  Советник по переходу обнаружил текущую установку [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — переход непосредственно к виртуальному каталогу сервера отчетов.  
  
||  
|-|  
|режим **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил, что текущая установка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это прямой просмотр виртуального каталога сервера отчетов, например **http://\<server name >/reportserver**. Не поддерживается в текущих версиях служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Это правило является предупреждением, обновление не заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Просмотрите с помощью пользовательского интерфейса SharePoint для библиотек документов или используйте **http://\<server name >/шарепоинт site >/_vti_bin/ReportServer**.  
  
  
