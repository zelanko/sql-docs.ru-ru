---
title: Страница ввода паролей (мастер добавления реплики) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9222f0b5d941cbdac38dc04afc3f770c9d487029
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="enter-passwords-page-add-replica-wizard"></a>Страница ввода паролей (мастер добавления реплики)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
