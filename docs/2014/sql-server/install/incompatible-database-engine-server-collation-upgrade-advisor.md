---
title: Несовместимые параметры сортировки ядро СУБД сервера (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: fbd4c1e55bb49c6ae8f75d3d12cc243df963018a
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952234"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Несовместимые параметры сортировки сервера компонента Database Engine (советник по переходу)
  Советник по переходу обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], настроенный на использование несовместимых параметров сортировки сервера.  
  
||  
|-|  
|режим **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], настроенный на использование несовместимых параметров сортировки сервера.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint использует архитектуру общих служб SharePoint. SharePoint не поддерживает компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], в котором задан учет регистра, параметры сортировки сервера или двоичные параметры сортировки сервера. В число несовместимых параметров сортировки входят те, которые по умолчанию учитывают регистр символов или являются двоичными, а также базовые параметры сортировки, которые по умолчанию являются совместимыми, но в них были заданы любые из следующих обозначений параметров сортировки.  
  
-   **Двоичный**  
  
-   **С учетом регистра**  
  
-   **Двоичный — codepoint**  
  
 Поскольку текущие параметры сортировки сервера компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] несовместимы, обновление заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Свойство параметров сортировки сервера компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] нельзя изменить. Выполнить обновление служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] невозможно. Необходимо перенести установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой сервер, на котором используются совместимые параметры сортировки сервера. Дополнительные сведения см. в следующих разделах:  
  
-   [Обновление и перенос служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Выбор параметров сортировки SQL Server](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
