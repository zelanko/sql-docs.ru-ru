---
title: Параметры сортировки сервера несовместимые Database Engine (Советник по переходу) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 5a81084ff6eba37d8a6fcc2643a760d879dcf13c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101661"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Несовместимые параметры сортировки сервера компонента Database Engine (советник по переходу)
  Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , настроенный на использование несовместимых параметров сортировки сервера.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , настроенный на использование несовместимых параметров сортировки сервера.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint использует архитектура общих служб SharePoint. SharePoint не поддерживает компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], в котором задан учет регистра, параметры сортировки сервера или двоичные параметры сортировки сервера. В число несовместимых параметров сортировки входят те, которые по умолчанию учитывают регистр символов или являются двоичными, а также базовые параметры сортировки, которые по умолчанию являются совместимыми, но в них были заданы любые из следующих обозначений параметров сортировки.  
  
-   **Двоичный**  
  
-   **С учетом регистра**  
  
-   **Двоичные по кодовым точкам**  
  
 Поскольку текущие параметры сортировки сервера компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] несовместимы, обновление заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Свойство параметров сортировки сервера компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] нельзя изменить. Выполнить обновление служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] невозможно. Необходимо перенести установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой сервер, на котором используются совместимые параметры сортировки сервера. Дополнительные сведения см. в следующих разделах:  
  
-   [Обновление и перенос служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [При выборе параметров сортировки SQL Server](http://go.microsoft.com/fwlink/?LinkId=233226)  
  
  