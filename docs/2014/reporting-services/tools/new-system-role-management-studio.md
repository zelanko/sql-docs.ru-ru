---
title: Создание системной роли (среда Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
caps.latest.revision: 27
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4d23cf7a0b557b4bbc687514b120af7a93cbf375
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083032"
---
# <a name="new-system-role-management-studio"></a>Создание системной роли (среда Management Studio)
  Используйте эту страницу, чтобы создать определение роли на уровне системы. Определение системной роли указывает набор задач на системном уровне, применимых к серверу отчетов в целом.  
  
> [!NOTE]  
>  Определения ролей используются только на сервере отчетов, работающем в собственном режиме. Если сервер отчетов настроен для интеграции с SharePoint, эта страница недоступна.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя определения роли. Имя определения роли должно быть уникальным в пределах пространства имен сервера отчетов. Имя должно содержать хотя бы одну букву или цифру. В него могут также входить пробелы и другие символы. При задании имени нельзя использовать следующие символы:  
  
 ; ? : \@ & = +, $ / * \< >  
  
 " /  
  
 **Описание**  
 Введите описание, объясняющее, как использовать роль, и перечисляющее функции, которые поддерживаются ролью.  
  
 **Задача**  
 Выберите задачи на уровне системы, которые могут выполняться посредством этой роли. Нельзя создавать новые задачи или изменять существующие, если они поддерживаются службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Нельзя выбирать задачи на уровне элемента для определения системной роли.  
  
 **Описание задачи**  
 Описание задачи с указанием поддерживаемых ею операций и разрешений.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Определение ролей](../security/role-definitions.md)  
  
  
