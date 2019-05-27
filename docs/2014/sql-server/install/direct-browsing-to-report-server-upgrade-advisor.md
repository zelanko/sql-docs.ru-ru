---
title: Прямой переход на сервер отчетов (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 870937f4dffe356ca2216335c74566efc73d2a52
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095537"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Прямой переход на сервер отчетов (советник по переходу)
  Помощник по обновлению обнаружил текущую установку [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] переходит напрямую в виртуальный каталог сервера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Помощник по обновлению обнаружил текущую установку [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] переходит напрямую виртуального каталога сервера отчетов, например **http://\<имя сервера > / ReportServer**. Не поддерживается в текущих версиях служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Это правило является предупреждением, обновление не заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Просмотр с помощью пользовательского интерфейса SharePoint для библиотек документов, или использовать **http://\<имя сервера > / сайт sharepoint >/_vti_bin/reportserver**.  
  
  
