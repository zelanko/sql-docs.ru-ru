---
title: На сервере отчетов обнаружены пользовательские элементы отчета (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5788b94356ec887b8c83850a4cb2c47d34b7388f
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952286"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>На сервере отчетов были обнаружены пользовательские элементы отчета (советник по переходу)
  Пользовательские элементы отчета, созданные для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], несовместимы с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Обновление может быть продолжено, но отчеты, использующие пользовательские элементы отчета, будут работать неправильно. Помощник по обновлению обнаружил пользовательские элементы отчета. Обновление может быть продолжено, но после завершения обновления необходимо вручную переместить файлы пользовательского элемента отчета в новую папку установки.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил пользовательские настройки расширения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в файлах конфигурации. Это указывает на то, что установка включает одну или несколько пользовательских сборок для отчетов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После завершения обновления вручную поместите файлы пользовательского элемента отчета в новую папку установки.  
  
## <a name="see-also"></a>См. также  
 [Советник по переходу Reporting Services проблем &#40;обновления&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
