---
title: Создание системной роли (среда Management Studio) | Документация Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9b9689be21565aa603433f20b1b445cb5f806c94
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823222"
---
# <a name="new-system-role-management-studio"></a>Создание системной роли (среда Management Studio)
  Используйте эту страницу, чтобы создать определение роли на уровне системы. Определение системной роли указывает набор задач на системном уровне, применимых к серверу отчетов в целом.  
  
> [!NOTE]  
>  Определения ролей используются только на сервере отчетов, работающем в собственном режиме. Если сервер отчетов настроен для интеграции с SharePoint, эта страница недоступна.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя определения роли. Имя определения роли должно быть уникальным в пределах пространства имен сервера отчетов. Имя должно содержать хотя бы одну букву или цифру. В него могут также входить пробелы и другие символы. При задании имени нельзя использовать следующие символы:  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **Описание**  
 Введите описание, объясняющее, как использовать роль, и перечисляющее функции, которые поддерживаются ролью.  
  
 **Задача**  
 Выберите задачи на уровне системы, которые могут выполняться посредством этой роли. Нельзя создавать новые задачи или изменять существующие, если они поддерживаются службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Нельзя выбирать задачи на уровне элемента для определения системной роли.  
  
 **Описание задачи**  
 Описание задачи с указанием поддерживаемых ею операций и разрешений.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Определение ролей](../../reporting-services/security/role-definitions.md)  
  
  
