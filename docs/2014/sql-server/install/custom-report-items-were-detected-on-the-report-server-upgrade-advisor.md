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
ms.openlocfilehash: feacf6aa6f233f85a67b43e7b72d3a50913991bf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059332"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>На сервере отчетов были обнаружены пользовательские элементы отчета (советник по переходу)
  Пользовательские элементы отчета, созданные для предыдущих версий, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] несовместимы с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Обновление может быть продолжено, но отчеты, использующие пользовательские элементы отчета, будут работать неправильно. Помощник по обновлению обнаружил пользовательские элементы отчета. Обновление может быть продолжено, но после завершения обновления необходимо вручную переместить файлы пользовательского элемента отчета в новую папку установки.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Советник по переходу обнаружил пользовательские настройки расширения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в файлах конфигурации. Это указывает на то, что установка включает одну или несколько пользовательских сборок для отчетов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После завершения обновления вручную поместите файлы пользовательского элемента отчета в новую папку установки.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
