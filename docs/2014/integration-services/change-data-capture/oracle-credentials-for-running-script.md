---
title: Учетные данные Oracle для выполнения скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 12de97bf147ccb61cde5f82e2fa31782404071e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771115"
---
# <a name="oracle-credentials-for-running-script"></a>Учетные данные Oracle для выполнения скрипта
  Чтобы запустить скрипт дополнительного журналирования Oracle из консоли конструктора CDC Oracle, программа запрашивает учетные данные пользователя Oracle, запускающего скрипт. Чтобы запустить этот скрипт, пользователь Oracle должен иметь разрешение ALTER TABLE для всех таблиц, которые будут отслеживаться, а также разрешение SELECT на представление DBA_LOG_GROUPS.  
  
## <a name="task-list"></a>Список задач  
 Введите в этом диалоговом окне следующие данные:  
  
 **Проверка подлинности**  
  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows**. Установите этот флажок, чтобы использовать текущие учетные данные домена Windows. Этот параметр можно использовать только в том случае, если в базе данных Oracle настроено использование проверки подлинности Windows.  
  
-   **Проверка подлинности Oracle**. Если выбран этот вариант, то нужно будет ввести **имя пользователя** и **пароль** в исходной базе данных Oracle, к которой устанавливается подключение.  
  
## <a name="see-also"></a>См. также  
 [Как управлять экземпляром CDC](manage-a-cdc-instance.md)   
 [Обзор и создание скриптов дополнительного журналирования](review-and-generate-supplemental-logging-scripts.md)  
  
  
