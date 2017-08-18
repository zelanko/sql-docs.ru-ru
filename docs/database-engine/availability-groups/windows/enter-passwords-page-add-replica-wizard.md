---
title: "Страница ввода паролей (мастер добавления реплики) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e89f1cedff6ee8b3a18e78ce08d5090331a5694
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="enter-passwords-page-add-replica-wizard"></a>Страница ввода паролей (мастер добавления реплики)
  В этом разделе справки описываются параметры, приведенные на странице **Ввод паролей** . Эта тема относится к [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Если реплики, выбранные на странице **Выбор реплик** , содержат базы данных с главным ключом, откроется страница "Ввод паролей".  
  
## <a name="enter-passwords-options"></a>Параметры ввода паролей  
 В сетке **Пользовательские базы данных в этом экземпляре SQL Server** перечислены все локальные пользовательские базы данных. Существуют следующие столбцы.  
  
 **Название**  
 Отображает имя локальной пользовательской базы данных.  
  
 **Размер**  
 Отображает размер базы данных, если он доступен мастеру.  
  
 **Состояние**  
 Указывает режим **Требуется пароль** для базы данных с главным ключом. Введя пароли для главных ключей базы данных в столбце **Пароли** , нажмите кнопку **Обновить**. Если пароли введены правильно, в столбце **Состояние** будет указано **Пароль введен**.  
  
 Если база данных не содержит главный ключ, в столбце **Состояние** будет указано **Пароль не требуется**.  
  
 **Пароль**  
 Если в столбце **Состояние** указано **Требуется пароль**, введите пароль для главного ключа базы данных.  
  
 **Обновить**  
 Щелкните, чтобы обновить сетку. Мы рекомендуем сделать это после ввода необходимых паролей.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  

