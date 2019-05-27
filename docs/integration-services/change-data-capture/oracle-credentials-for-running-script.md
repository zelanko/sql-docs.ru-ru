---
title: Учетные данные Oracle для выполнения скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ae98170e3c6628afc75934cece345bbbfbc22267
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728645"
---
# <a name="oracle-credentials-for-running-script"></a>Учетные данные Oracle для выполнения скрипта

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Чтобы запустить скрипт дополнительного журналирования Oracle из консоли конструктора CDC Oracle, программа запрашивает учетные данные пользователя Oracle, запускающего скрипт. Чтобы запустить этот скрипт, пользователь Oracle должен иметь разрешение ALTER TABLE для всех таблиц, которые будут отслеживаться, а также разрешение SELECT на представление DBA_LOG_GROUPS.  
  
## <a name="task-list"></a>Список задач  
 Введите в этом диалоговом окне следующие данные:  
  
 **Проверка подлинности**  
  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows**. Выберите этот параметр, чтобы использовать учетные данные текущего пользователя Windows. Этот параметр можно использовать только в том случае, если в базе данных Oracle настроено использование проверки подлинности Windows.  
  
-   **Проверка подлинности Oracle**. Если выбран этот вариант, то нужно будет ввести **имя пользователя** и **пароль** в исходной базе данных Oracle, к которой устанавливается подключение.  
  
## <a name="see-also"></a>См. также:  
 [Как управлять экземпляром CDC](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Обзор и создание скриптов дополнительного журналирования](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
