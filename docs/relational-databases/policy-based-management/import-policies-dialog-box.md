---
title: "Диалоговое окно \"Импорт политик\" | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7719420505e002b9961fda5c88e379568b5649f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="import-policies-dialog-box"></a>Диалоговое окно «Импорт политик»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это диалоговое окно используется для импорта одной или нескольких политик (и упоминаемого в них условия), сохраненных в виде XML-файлов, в текущий экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Файлы, подлежащие импорту**  
 Чтобы выполнить импорт политики из XML-файла, введите путь и имя файла или нажмите кнопку "Обзор" (**...**).  
  
 **Заменять дубликаты импортируемыми элементами**  
 Выберите, чтобы перезаписать любую существующую политику или условие с тем же именем, если они уже существуют в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Перезаписать условие с зависимой политикой можно только в том случае, если зависимая политика также переписывается. Если данный параметр не выбран, то наличие условия с таким же выражением не вызовет ошибку.  
  
 **Состояние политики**  
 Выберите требуемое состояние для импортированной политики:  
  
-   **Сохранить состояние политики при импорте**  
  
-   **Включить все политики при импорте**  
  
-   **Выключить все политики при импорте**  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Импорт политики управления на основе политик](../../relational-databases/policy-based-management/import-a-policy-based-management-policy.md)   
 [Экспорт политики управления на основе политик](../../relational-databases/policy-based-management/export-a-policy-based-management-policy.md)  
  
  
