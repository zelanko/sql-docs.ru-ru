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
ms.openlocfilehash: 9a12f39bc399e2c46e61fc290bb20ad2c43e4de9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012549"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Прямой переход на сервер отчетов (советник по переходу)
  Советник по переходу обнаружил, что текущая установка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — Просмотр непосредственно в виртуальном каталоге сервера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил, что текущая установка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] находится непосредственно в виртуальном каталоге сервера отчетов, например **http:// \<server name> /ReportServer**. Не поддерживается в текущих версиях служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Это правило является предупреждением, обновление не заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Просмотр с помощью пользовательского интерфейса SharePoint для библиотек документов или использование **http:// \<server name> /шарепоинт site>/_vti_bin/ReportServer**.  
  
  
