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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952209"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Прямой переход на сервер отчетов (советник по переходу)
  Советник по переходу обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , что текущая установка — просмотр непосредственно в виртуальном каталоге сервера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил, что [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] текущая установка находится непосредственно в виртуальном каталоге сервера отчетов, например **http://\<Server Name>/ReportServer**. Не поддерживается в текущих версиях служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Это правило является предупреждением, обновление не заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Просмотрите с помощью пользовательского интерфейса SharePoint для библиотек документов или используйте **имя\<сервера http://>/шарепоинт site>/_vti_bin/ReportServer**.  
  
  
